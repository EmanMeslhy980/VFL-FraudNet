# VFL-FraudNet
Fraud detection in healthcare is hard in a multi-cloud setting. Data is split across hospitals, insurers, and pharmacies. Privacy rules stop them from sharing raw files. Also, human investigators must review outcomes after the model runs. They have to sort through many cases, including rare ones.

Vertical federated learning helps in this setup. Each party holds different parts of the same patient data. The parties train using a shared patient id while keeping their own features private. Even so, the usual vertical method can still be attacked. It may also miss the uncommon signs that deserve early human attention.

We introduce VFL-FraudNet. The goal is to make the training more careful and more risk focused. We add a risk-aware gate to shift latent signals toward rare high-risk patterns. This makes it easier to flag items for later audit. We also use a zero-trust style aggregation. Each client update is checked against live norm stats. Updates that look odd get less weight. As an extra safeguard, we use Krum as a second step.

To protect privacy, we clip and perturb gradients. The perturbation follows a Gaussian mechanism under differential privacy. This gives formal privacy guarantees.

On a patient-level CMS Medicare test with 37,418 patients, VFL-FraudNet reaches 97.52 ± 0.36% accuracy. It keeps 99.8% of the centralized upper bound, 97.69 ± 0.24%. In contrast, horizontal FL falls to 72.73 ± 2.65%.

We also test byzantine poisoning. In a ten-client horizontal setup, 30% of clients are compromised. VFL-FraudNet stays accurate. The undefended horizontal method drops to 8.39%.

For privacy budget, we use the smallest tested setting. With epsilon around 0.14 and subsampled RDP accounting, VFL-FraudNet keeps 84.13% of the accuracy. Centralized training keeps 37.24%. That yields about a 47 point resilience gain.

VFL-FraudNet acts as a privacy-safe decision support tool for healthcare fraud review, and it is built to handle hostile updates too.
<img width="1408" height="768" alt="Model" src="https://github.com/user-attachments/assets/f314d7c4-4ce9-409e-b3d2-b367be8b5a6a" />
