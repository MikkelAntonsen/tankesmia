### Finne og formatere annotasjonsfiler for regression test dataset

Brukte følgende kommando
```
for file in (ls Val/Salmon_AdultFemale_AnalFin/ann/ | head -n 6 | awk '{print $NF}'); file $REPOSET_PATH/imagelake/(basename $file .json); end
```
for å liste de 6 første annotasjonsfilene i et dataset og gjøre det klart at de eksisterte i  reposet imagelake.

Læringsmomenter:
1. ls lister bare filer og output er faktisk linjebasert og har columns, selv om det ikke ser sånn ut (i forhold til ls -al f.eks.)
2. Head funker bedre med `ls` enn med `ls -al`
3. jeg kan ikke awk men [`NF is a predefined variable whose value is the number of fields in the current record. `awk` automatically updates the value of `NF` each time it reads a record.`](https://www.gnu.org/software/gawk/manual/gawk.html#SEC_Contents)
4. basename er nyttig i fish for å fjerne file extensions 

### Endelig kommando for å laste opp alle bilder til s3 stingray machine learning imagelake

```
aws s3 cp /volumenta/reposet/imagelake/00a75ea2-fb75-4356-857a-5560722f3f23_LeftCamera_019.jpg s3://stingray-machine-learning-imagelake
```