# tytonate

A database of BED files for masking reference sequences in public health microbial genomics

## Generating the BED file

In most cases, we generate the file by masking known phage in the reference
sequence. We identify phage by using the [PHASTER](https://phaster.ca) online
service.

*PHASTER* provides phage position in 1-based code. This means that both the
start and end position are included and that the start of the sequence is
labelled with 1. So, in the sequence below, a phage in positions 3-5 would
have sequence CGC:

    A T C G C G
    1 2 3 4 5 6

**HOWEVER**, BED files are have a start position 0-based (included) and an
end position 1-based (excluded). So, in the same example above *phaster*
position 3-5 would be translated to 2-5 (i.e., subtract 1 from the start
position, but leave the end position alone):

    0 1 2 3 4 5
    A T C G C G
    1 2 3 4 5 6

Thus, when translating positions from *phaster* to BED format, we subtract 1
from the start position, and leave the end position as is. Where needed, similar
translations will be done in order to make sure the BED format is correctly
coded.

## Database structure

The database is structured by Genus labelled folders, with subfolders indicating
relevant subgroups (e.g., ST, Serovar, species).

Unless otherwise specified,
the following *genera* are taken as shorthand for specific species of interest
to public health:

* Salmonella --- *Salmonella enterica subsp enterica*
* Listeria --- *Listeria monocytogenes*

# Naming convention

The DB is named after the Australian Masked Owl (*Tyto novaehollandiae*). The
goal is to build a database of sites frequently *masked* when identifiying
genetic variation suitable for phylogenetic analyses in public health
microbial genomics.
