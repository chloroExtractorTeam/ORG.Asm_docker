# ORG.Asm_docker
A docker solution for ORG.Asm (https://git.metabarcoding.org/org-asm/org-asm)

As installation of the Organelle Assembler ORG.Asm consistently failed on basically every machine I tried, here is a minimal docker image which successfully installs it in a fresh container.

To use it do the following:

## Build the docker container
```
cd docker
docker build --tag orgasm .
```

## Test it with the sample dataset
```
docker run --rm -it orgasm bash
oa index --estimate-length=0.9 butterfly /org-asm/samples/papi_R1.fastq.gz /org-asm/samples/papi_R2.fastq.gz
oa buildgraph --probes protMitoMachaon butterfly butterfly.mito
oa unfold butterfly butterfly.mito
```

## Run it with own data (chloroplast)
```
docker run -v $PWD/data:/data --rm -it orgasm bash
cd /data
oa index own own_R1.fastq own_R2.fastq
oa buildgraph --probes protChloroArabidopsis own own.chl
oa unfold own own.chl
```

## License
This repository is available under [MIT License](LICENSE).
The ORG.Asm is distributed under a separate license, see https://git.metabarcoding.org/org-asm/org-asm
