# Information about this repository
This repository is a fork of the latest version of [ExpansionHunter (v5.0.0)](https://github.com/Illumina/ExpansionHunter) and includes the following modifications:
1. By default, it treats the following errors as warnings and does not terminate the program: _"Error loading locus x: Flanks can contain at most 5 characters N but found x Ns.", "Invalid contig name." and "Unable to extract X from Y."_. 
2. The VCF files now include an `SVTYPE=STR` info field for each locus (was absent in the original program).
3. Users can specify the sample ID from the command line using the `--sample-id` parameter, e.g., `--sample-id ABCD1234`. By default, if not specified, the sample ID is derived from the file name.
4. Compiling the program uses updated libraries that should resolve some issues when building the application that happened with older ones.

## Other useful resources
- [Tools for ExpansionHunter](https://gitlab.com/andreassh/tools-for-expansionhunter) repository has scripts for annotating VCF files with disease information as well as converting BED files into variant catalogues.
- [STRipy's ExpansionHunter Results Analyzer](https://stripy.org/expansionhunter-results-analyzer) allows to easily and quickly assess results from the ExpansionHunter's output files.
- [STRipy's ExpansionHunter Catalogue Creator](https://stripy.org/expansionhunter-results-analyzer) helps to create custom variant catalogues for different referent genomes.

---

# Expansion Hunter: a tool for estimating repeat sizes

There are a number of regions in the human genome consisting of repetitions of
short unit sequence (commonly a trimer). Such repeat regions can expand to a
size much larger than the read length and thereby cause a disease.
[Fragile X Syndrome](https://en.wikipedia.org/wiki/Fragile_X_syndrome),
[ALS](https://en.wikipedia.org/wiki/Amyotrophic_lateral_sclerosis), and
[Huntington's Disease](https://en.wikipedia.org/wiki/Huntington%27s_disease)
are well known examples.

Expansion Hunter aims to estimate sizes of such repeats by performing a targeted
search through a BAM/CRAM file for reads that span, flank, and are fully
contained in each repeat.

Linux and macOS operating systems are currently supported.

## License

Expansion Hunter is provided under the terms and conditions of the
[Apache License Version 2.0](LICENSE.txt). It relies on several third party
packages provided under other open source licenses, please see
[COPYRIGHT.txt](COPYRIGHT.txt) for additional details.

## Documentation

Installation instructions, usage guide, and description of file formats are
contained in the [docs folder](docs/01_Introduction.md).

## Companion tools and resources

- [A genome-wide STR catalog](https://github.com/Illumina/RepeatCatalogs)
  containing polymorphic repeats with similar properties to known pathogenic and
  functional STRs
- [REViewer](https://github.com/Illumina/REViewer), a tool for visualizing
  alignments of reads in regions containing tandem repeats

## Method

The method is described in the following papers:

- Egor Dolzhenko, Joke van Vugt, Richard Shaw, Mitch Bekritsky, and others,
  [Detection of long repeat expansions from PCR-free whole-genome sequence data](http://genome.cshlp.org/content/27/11/1895),
  Genome Research 2017

- Egor Dolzhenko, Viraj Deshpande, Felix Schlesinger, Peter Krusche, Roman Petrovski, and others,
[ExpansionHunter: A sequence-graph based tool to analyze variation in short tandem repeat regions](https://academic.oup.com/bioinformatics/article/doi/10.1093/bioinformatics/btz431/5499079),
Bioinformatics 2019
