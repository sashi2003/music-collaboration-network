# Collaboration Networks in the Music Industry

A network analysis of artist collaboration patterns using a nested
Exponential Random Graph Model (ERGM).

## Research Question

Music collaborations form complex social networks shaped by artistic
similarity, industry dynamics, and shared professional connections.
This project asks:

- Do artists from the same country collaborate more frequently?
- Does genre similarity influence collaborations?
- Does network structure increase the likelihood of collaboration
  formation?

## Data

- Publicly available Kaggle music collaboration dataset
- **Top 150 most collaborative artists** selected
- **Undirected** artist collaboration network (edges = collaborations)
- Artist attributes: country, genre group, collaboration count

## Method

A **nested Exponential Random Graph Model (ERGM)** was used to examine
collaboration tie formation, incorporating structural and
attribute-based effects estimated incrementally:

- Country homophily
- Genre homophily
- Collaboration activity (count)
- Triadic closure via `gwesp`

## Results

| Term              | Estimate | Interpretation                              |
|-------------------|---------:|----------------------------------------------|
| Country Homophily |  +0.895  | Same-country artists collaborated more frequently |
| Genre Homophily   |  +0.995  | Artists sharing genres were more likely to collaborate |
| Collaboration Count | +0.003 | Highly collaborative artists formed additional ties |
| GWESP             |  +1.862  | Strong clustering and triadic closure were present |

Goodness-of-fit diagnostics confirmed the model reproduced key
structural properties of the observed network, including degree
distributions, shared partner structures, and geodesic distances.

**Key takeaway:** Collaboration in the music industry is not random.
It's shaped by shared characteristics (country, genre) as well as
endogenous network processes like clustering and repeated partnership
formation.

## Repo Structure

```
music-collaboration-network/
├── README.md
├── analysis.qmd   # Data prep, ERGM, diagnostics, plots
├── poster.pdf      # Final research poster
└── data/           # Add artists.csv and collaborations.csv here
```

## Reproducing

1. Clone the repo
2. Add `artists.csv` and `collaborations.csv` to `data/`
3. Open `analysis.qmd` in RStudio or run with Quarto:

```bash
quarto render analysis.qmd
```

Requires R packages: `statnet`, `network`, `ergm`, `igraph`, `ggplot2`

## Poster

See [`poster.pdf`](poster.pdf) for the full research poster, including
methodology, goodness-of-fit diagnostics, key findings, and future
work.

## Future Work

- Incorporating temporal dynamics to examine how collaboration
  patterns evolve over time
- Expanding the network to include additional artist attributes such
  as record labels and streaming popularity
- Modeling weighted collaborations based on collaboration frequency or
  commercial success of tracks
