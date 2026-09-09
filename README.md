# Audit SIA™ — Landing page / funnel Facebook

Deux pages statiques autonomes, aucune étape de build :
- `index.html` — landing (VSL + quiz + formulaire)
- `merci.html` — page de remerciement (`/merci`) avec Calendly, atteinte uniquement après une soumission réussie

## Déployer sur Vercel
1. Pousser ce dossier à la racine du dépôt `charlesdumont-web/Sales-Funnel` (branche `main`).
2. Vercel → Add New Project → importer `Sales-Funnel` → Framework preset : **Other** → Deploy.
3. Ajouter le domaine dans Settings → Domains.

## Intégrations déjà câblées
- **Pixel Meta** `4466727666988945` : code de base sur les deux pages (`PageView`). `Lead` se déclenche **uniquement au chargement de `/merci`** (jamais au clic sur le bouton — le formulaire redirige vers `/merci` seulement après validation et envoi réussis). `Schedule` à la confirmation Calendly (événement `calendly.event_scheduled`, écouté sur `/merci`).
- **Calendly** : https://calendly.com/charles-dumont-synchroia/appel-audit-synchro-ia (nom, courriel et téléphone préremplis).
- **VSL** : YouTube W8AA7YqGMPg (embed nocookie).

## À faire avant la campagne
- **Destination du formulaire** : la page envoie un POST JSON (prénom, nom, entreprise, courriel, téléphone, taille, rôle, échéancier, source, page, submittedAt) vers `webhookUrl`. Actuellement vide → les coordonnées ne sont conservées que dans le préremplissage Calendly. Fournir une URL (Make / n8n / Zapier / Formspree) et régénérer la page.
- Remplacer les liens `#` du pied de page (confidentialité, conditions).
- Tester les événements avec l'extension Meta Pixel Helper, puis envoyer l'URL finale à l'agence.
