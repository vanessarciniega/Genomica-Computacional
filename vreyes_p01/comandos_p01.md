# Comandos de la Práctica 01
## Vanessa Angélica Reyes Arciniega

# Parte I. 

**Respuesta 1:**  
* echo $SHELL  
/bin/bash  
* echo $0  
-bash 

**Respuesta 2:**  
* mkdir data filtered raw_data meta scripts figures archive  

**Respuesta 3:**  
* mv filtered data/
* mv raw_data data/

**Respuesta 4:**

La organización de esta manera favorece que tengamos bien estructurado lo que tenemos en nuestro directorio bioinformático a través de subdirectorios para categorizar adecuadamente los múltiples datos, figuras y archivos con los que vamos a estar trabajando a lo largo del curso y eventualmente en el proyecto. Y todo ello no sólo nos ayuda a nosotros a identificar de forma más rápida y fácil la información sino también a cualquier otra persona con quien lo compartamos porque la organización tiene una lógica con los subdirectorios esenciales de cualquier proyecto bioinformático.

# Parte II.

**Respuesta 1:**  
* chmod u+x delay.sh

**Respuesta 2:**  
* ls -l delay.sh  
-rwxr--r-- 1 vane vane 93 Oct 21 11:43 delay.sh
* ./delay.sh  
Después de la Parte I. necesito un descanso de exactamente 30 segundos.

**Respuesta 3:**  
* nano delay.sh  
echo "Después de la Parte I. necesito un descanso de exactamente 30 segundos." && sleep 30 && echo "Ya puedo continuar!"
* ./delay.sh  
Después de la Parte I. necesito un descanso de exactamente 30 segundos.  
Ya puedo continuar!

**Respuesta 4:**
* nano delay.sh  
echo "Después de la Parte I. necesito un descanso de exactamente 30 segundos." && sleep 300 && echo "Ya puedo continuar!"
* ./delay.sh &  
[1] 428
* kill -9 428

# Parte III.

**Respuesta 1:**
* nano SarsCov-2.txt  

**Respuesta 2:**

* mv sequence.fasta sarscov2_genome.fasta
* mv sequence.gff3 sarscov2_genome.gff3  

* mv sequence.fasta splike_c.faa
* mv sequence(1).fasta splike_b.faa
* mv sequence(2).fasta splike_a.faa

* nano SarsCov-2_Spike.txt

* mv *.faa ~/GenomicaComputacional/vreyes_p01/data/raw_data/
* mv *.fastq.gz ~/GenomicaComputacional/vreyes_p01/data/raw_data/
* mv sarscov2_assembly.fasta.gz ~/GenomicaComputacional/vreyes_p01/data/raw_data/
* mv sarscov2_genome.fasta ~/GenomicaComputacional/vreyes_p01/data/raw_data/
* mv sarscov2_genome.gff3 ~/GenomicaComputacional/vreyes_p01/data/raw_data/

# Parte IV. 

**Respuesta 1:**
* ln -s ~/GenomicaComputacional/vreyes_p01/data/raw_data/splike_c.faa filtered
* ln -s ~/GenomicaComputacional/vreyes_p01/data/raw_data/splike_b.faa filtered
* ln -s ~/GenomicaComputacional/vreyes_p01/data/raw_data/splike_a.faa filtered

**Respuesta 2:**
* touch glycoproteins.faa

**Respuesta 3:**
* head -n1 splike_a.faa  
pdb|6VXX|A Chain A, SARS-CoV-2 spike glycoprotein
* head -n1 splike_b.faa  
pdb|6VXX|B Chain B, SARS-CoV-2 spike glycoprotein
* head -n1 splike_c.faa  
pdb|6VXX|C Chain C, SARS-CoV-2 spike glycoprotein

**Respuesta 4:**
* cat splike_a.faa splike_b.faa splike_c.faa > glycoproteins.faa

**Respuesta 5:**
* Las ligas simbólicas suaves se rompieron.

**Respuesta 6:**
* cat sarscov2_genome.fasta | head -n3  
NC_045512.2 Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome
ATTAAAGGTTTATACCTTCCCAGGTAACAAACCAACCAACTTTCGATCTCTTGTAGATCTGTTCTCTAAA
CGAACTTTAAAATCTGTGTGGCTGTCACTCGGCTGCATGCTTAGTGCACTCACGCAGTATAATTAATAAC
* zless sarscov2_assembly.fasta.gz | head -n3  
NODE_1_length_264_cov_161.042781
CACAAATCTTAACACTCTTCCCTACACGACGCTCTTCCGATCTACGCCGGGCCATTCGTA
CGAACCGATACCTGTGGTAAAGGGTCCTACTGTATGGTGGTACACGAGTAGTAGCAAATG
* El archivo .fasta.gz es un archivo de ensamblaje de secuencias, por lo que naturalmente contiene un mayor número de lecturas cortas que en realidad son fragmentos de secuencia del DNA que se pretende reconstruir. 
Por su parte, el archivo .fasta ya es la secuencia completa, por lo que es una sola lectura. 

**Respuesta 7:**
* grep '>' sarscov2_genome.fasta | wc -l  
1
* zless sarscov2_assembly.fasta.gz | grep '>' | wc -l  
35

**Respuesta 8:**
* zless SRR10971381_R2.fastq.gz | head -n12  
@SRR10971381.512_2
CGTGGAGTATGGCTACATACTACTTATTTGATGAGTCTGGTGAGTTTAAAGTGGCTTCACATATGTATTGTTCTTTCTACCCTCCAGATGAGGATGAAGAAGAAGGTGATTGTGAAGAAGAAGAGTTTGAGCCATCAACTCAATATGAGT  
'+'
/FFFA/A/FFFF66FFFFFF/FF/FFFFFFFFFFFFF/AFFF6FFFA6FFFFF/FFFFFFFFFFFFFFFFFF/FF/FFFFFA/FFF/FFF/A/AFA/FFFFF/=F/F/F/AFAFF//A/AFF//FFAF/FFF=FFAFFFA/A/6=///==  
@SRR10971381.556_2
TTTGTAAAAATAAAATAAAAAAAATAAAAATAATATATTAAAAAAAGATAAATAAAAAAATGAACAATTAATAAAAAAAAAAAAAAAAAAAAATTAAAAAAAAAAAAAAAAAAAATAAAAAAAAAAAAAAATAAAAAAAAAATTATAAAA  
'+'  
6AFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF/FFFAFFFFFF/FFA/FF=F//=FF/FFFFFFFFFFFFFA/FFFF/FF/FA//F/FFFFFFA/=FFFFF/FFFF/F=FFFAFF///FFFFA/FF/6//////=/  
@SRR10971381.1428_2  
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA  
'+'  
FFFFFFFFFFFFAFFFAFFFFFF6A//F//FFF
* zless SRR10971381_R2.fastq.gz | grep '@' | wc -l  
130022

**Respuesta 9:**  
La extensión .fasta y .faa hacen referencia al formato FASTA que presenta secuencias de nucleótidos o aminoácidos, el archivo .fastq representa secuencias de nucleótidos. 
En el formato FASTA una secuencia comienza con una línea de cabecera con '>' que indica el ID de secuencia y la descripción, seguida por líneas de datos de secuencia. No debería existir espacio entre el '>' y la primera letra del identificador. 
En el formato FASTA se recomienda que todas las líneas de texto sean menores de 80 caracteres, mientras que en FASTQ la secuencia y los puntajes de calidad generalmente se colocan en una sola línea cada uno.

Un registro FASTQ tiene el siguiente formato:  
-Una línea que comienza con @, que contiene el ID de secuencia.  
-Una o más líneas que contienen la secuencia.  
-Una nueva línea que comienza con el carácter + y que está vacía o repite el ID de secuencia.   
-Una o más líneas que contienen las puntuaciones de calidad.

**Respuesta 10:**
* Con less el "sobrante" de la información sobre la secuencia lo pone en la siguienta línea, mientras que less -S corta ese "sobrante".

**Respuesta 11:**
* grep 'gene' sarscov2_genome.gff3 | cut -f3 | wc -l  
28
La diferencia entre gene y CD es que CD (coding sequence) es únicamente la región codificante del gen o el conjunto de exones, la región que se traduce, y 'gene' representa todo el gen, incluyendo intrones y exones.
