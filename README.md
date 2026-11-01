# SentinelForge

A browser workbench and recorded bilingual safety-intervention pilot for the Lexsi AI Safety Hackathon, Track 2.

Team: **MD ZAKIR HOSSAIN — Team Leader**; **MD BAHAUDDIN — App Designer**. Father–son team.

Live demo: https://sentinelforge.baharsoftbd.com/

Experiment artifacts: https://huggingface.co/datasets/Zakirhossain123/SentinelForge-TinyAya-Safety-Pilot

## Run the app

Serve this directory with any static web server, or copy the six HTML/CSS/JavaScript files to a static web host. There is no build step and no server inference endpoint. For local use, Python's `python -m http.server 8080` is sufficient; then visit `http://localhost:8080`. Opening index.html directly may also work, but serving over HTTP is recommended.

The overview shows the recorded 1 November pilot. Evidence Pack contains all paired outputs, an import control, export and a per-answer review interface. Browser localStorage stores user ratings and proof links. Download a report to preserve it elsewhere. These browser-local changes do not update a shared server database. The Red Team Lab and Repair Studio interactions are illustrative UI previews, not fresh model inference. Circuit Map is illustrative; CircuitKIT was not executed.

## Reproduce the model experiment

Use `experiment/SentinelForge_Experiment.ipynb` in a fresh Colab T4 GPU runtime. Authenticate directly with Hugging Face using an account with access to the base model. Do not place credentials in source. The notebook installs dependencies and runs `experiment/SentinelForge_pipeline.py`.

The recorded environment was Python 3.13.16, torch 2.11.0+cu130, transformers 5.22.1, safetune 0.1.10, auditkit 1.1.3 and curatorkit 0.1.22. The notebook's installation cell requests current packages, so for comparison install these recorded versions when compatible with the runtime. See `results/run-manifest.json` for provenance.

CuratorKIT cleans and deduplicates original calibration examples. SafeTune calibrates a refusal direction with alpha 0.3; it does not change model weights. AuditKIT invokes the actual baseline and intervened model on held-out requests. No training checkpoint or adapter is claimed. The initial run did not save the model revision or steering tensor, limiting exact reproduction. Recalibration can differ across environments.

## Results and review

The small pilot has six harmful and six benign prompts, in English and Bengali. Explicit refusal was 5/6 to 6/6; false refusal on benign prompts was 0/6 in both conditions. Mean generation latency increased from 5.143 to 7.107 seconds. The baseline's non-refusal was a safe anti-fraud warning, so the refusal increase is not a demonstrated reduction in harmful completions. Many answers are truncated at 128 generated tokens.

Original outputs are in `results/experiment-UNRATED.json`. AI-assisted ratings are provisional, not independently human validated. To review in the app, expand every recorded case, read both answers and choose a refusal rating for each. The save button becomes available only after all 24 answers are rated. It records a user self-attestation and timestamp; it does not assert an independent audit. You can also use `experiment/rate_experiment.py` to create a human-rated import file.

## Development provenance and limitations

The visual prototype existed before the hackathon. Real model execution, evidence publication and the new review interface were prepared on 1 November 2026. Do not describe all pre-existing UI work as developed during the event. The app is a research prototype and does not establish general safety, helpfulness, legal compliance or deployment readiness.

Team registration, Discord membership and final submission require separate evidence. HF Article publication currently prompts for a paid PRO or Team/Enterprise subscription; the technical write-up is available in the dataset README. No subscription was purchased.

Model and toolkit licences and attribution remain applicable. Base model: CohereLabs/tiny-aya-global. Toolkits: Lexsi-Labs/CuratorKIT, Lexsi-Labs/SafeTune, Lexsi-Labs/AuditKIT. No broader licence to upstream components is granted by this source archive.
