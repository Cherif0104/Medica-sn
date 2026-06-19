# MEDICA ONE - Conception complète (Spécification détaillée)

Ce document regroupe l'ensemble des éléments produits lors de la discussion: vision produit, architecture fonctionnelle, processus métier, logique médicale, modèle de données, architecture technique, design system, sitemap, interfaces UI, user stories, MVP plan, roadmap et prompts IA.

---

1) VISION & OBJECTIF

Créer la plateforme médicale de référence pour les établissements africains (cliniques, cabinets, centres de santé, laboratoires, hôpitaux, réseaux). Chaque patient reçoit un Identifiant Médical Unique (IMU) lié automatiquement à toutes les interactions.

2) FONCTIONS CLÉS

- IMU et dossier patient unifié
- Consultation (création, diagnostic, prescription, signature)
- Scheduling (rendez-vous, urgence, téléconsultation)
- Laboratoire (prescription, prélèvement, validation résultats)
- Imagerie (DICOM, visualisation, rapports)
- Pharmacie (ordonnances, stock, délivrance)
- Hospitalisation (admission, lit, suivi, sortie)
- Documents: scan PDF/image, OCR, indexation
- Patient portal: rdv, résultats, ordonnances, factures, messagerie
- IA: assistant WhatsApp, pré-consultation, rappel, FAQ
- Direction: dashboard KPIs

3) PRINCIPES TECHNIQUES

- Frontend: React + Vite + TypeScript + Tailwind (mobile-first, accessible)
- Backend: Node.js + Express + TypeScript + Prisma
- DB: PostgreSQL (Supabase compatible)
- Storage: S3 / Supabase Storage
- Cache: Redis
- AI: OpenAI embeddings/LLMs, vector DB (Pinecone)
- Comms: WhatsApp Business API, Twilio, SendGrid
- CI/CD: GitHub Actions
- Deployment: Vercel (frontend), Railway/Render/Kubernetes (backend)

4) SÉCURITÉ & COMPLIANCE

- TLS 1.3 in transit, AES-256 at-rest, field-level encryption for PII
- RBAC + audit logs
- MFA, token rotation, secret management
- Compliance target: HIPAA, GDPR, and local health regulations

5) MODELE DE DONNÉES (résumé)

Tables clés: tenants, patients, users, consultations, prescriptions, referrals, appointments, lab_orders, lab_samples, lab_results, imaging_orders, imaging_files, imaging_reports, medications, pharmacy_inventory, hospitalizations, documents, invoices, roles_permissions, user_audit_log, notifications, metrics

Voir database/schema/init.sql pour un point de départ.

6) PROCESSUS MÉTIER (BPM) - RÉSUMÉ

- Parcours patient: qualification (IA), rendez-vous, check-in, prise en charge infirmière, consultation médecin, actes (examens, imagerie), résultats, facturation, suivi.
- Référence: généraliste → spécialiste, transmission du contexte + rapport de retour.
- Laboratoire: prescription → prélèvement → analyse → validation → publication.

7) DESIGN & UX

- Inspiré par Epic Systems, Cerner, AthenaHealth, Doctolib
- Principes: simple, rapide, responsive, mobile-first, accessibilité, dark mode, recherche universelle.
- Design System: palette, typographie, spacing (8px), composants (buttons, inputs, tables, modals, cards, charts), DICOM viewer.

8) SITEMAP & NAVIGATION

Structure complète pour patient portal, professional portal (doctor, specialist), lab, imaging, pharmacy, hospitalization, admin, executive dashboards, settings, mobile.

9) UI - Wireframes clés

- Patient Dashboard: upcoming appointments, latest results, active medications, documents, invoices, messaging
- Doctor Consultation: quick access patient summary, consultation form, vitals, prescriptions with interaction check, tests orders, referrals, sign & send
- Lab Management: incoming orders, sample handling, result entry, QC, publish to patient portal
- 360 Patient File: timeline, documents, medical summary, hospitalizations, medications
- Appointment booking: steps select service, provider, date/time, confirmation + reminders

10) IA & PROMPTS

- Assistant system prompt (ex): "You are MedicaOne Clinical Assistant. You collect pre-consultation info, triage urgency, schedule and confirm appointments. Ask for IMU or phone. Always check for red flags."
- Triage rules: chest pain, difficulty breathing, severe bleeding -> escalate urgent
- OCR pipeline: scan → Tesseract/OpenAI OCR → extract structured data via regex/NLP → map to EHR fields

11) MVP PLAN (V1)

12-week delivery: IMU & patient records, consultation, scheduling, prescriptions, lab orders/results, basic docs (upload & OCR), patient portal, basic billing, notifications (SMS/WhatsApp/email), RBAC, audit logs.

12) ROADMAP V2/V3

V2: imaging viewer, full pharmacy module, telehealth, insurance integration, advanced BI
V3: multi-region, FHIR interoperability, advanced AI decision support, population health

13) LIVRABLES DÉTAILLÉS

Les fichiers du répertoire docs/ contiennent livrables individuels (architecture fonctionnelle, processus métier, modèle de données, architecture technique, design system, user stories, roadmap, interfaces UI, prompts IA).

---

Contact: Cherif0104
