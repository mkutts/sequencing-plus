# Sequencing+

Sequencing+ is a baseball analytics research project designed to quantify the effectiveness of pitch sequencing in MLB, beyond traditional stuff-based models like Stuff+. This metric captures how the order of pitches affects hitter outcomes — particularly for pitchers who set up non-fastball sequences.

## Features

- Pitch pair analysis (Pitch N−1 → Pitch N)
- Normalized league baselines for pitch combinations
- Output metrics: Whiff%, xwOBA, CSW%, Run Value deltas
- Compatible with Statcast data via pybaseball

## Repository Structure

- `sequencing_plus/`: Core logic and metric computation
- `notebooks/`: Jupyter notebooks for exploration and validation
- `data/`: Local data files (not tracked)
- `tests/`: Unit and integration tests

## Getting Started

```bash
git clone https://github.com/your-username/sequencing-plus.git
cd sequencing-plus
pip install -r requirements.txt
# sequencing-plus

## 📄 Project Proposal

The full research proposal for Sequencing+ is available [here](docs/sequencing_plus_proposal.md). It outlines the motivation, methodology, metric design, validation strategy, and timeline.

