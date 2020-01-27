## _De novo_ transcriptome assembly with Trinity

Make a new subdirectory in your ```/scratch/genomics/<username>/rnaseq``` directory for running trinity.

```
$ mkdir trinity
$ cd trinity
```

###Trinity _de novo_ assembly

####Instructions for Job Submission (qsub):
<details><summary>Instructions for Job Submission</summary>
<p>

 First open the [QSubGen web application](https://hydra-admin01.si.edu/tools/QSubGen/).

- Choose medium time limit and reserve 6GB of memory.
- Select 'multi-thread' and choose 4 CPUs.
- Total memory requested will be 24GB
- In the modules field, type ```trinity``` and the select the module ```bioinformatics/trinity/2.8.5```.
- In job specific commands, type:
          
      	Trinity --seqType fq \
      	--left ../data/RNA_Eye_1.fastq \
      	--right ../data/RNA_Eye_2.fastq \
      	--max_memory 24G --CPU $NSLOTS \
      	--output RNA_Eye.trinity \
      	--trimmomatic --full_cleanup 

- Choose a descriptive job name then click on 
- ```Check if OK```
- If it passes, either save it and upload it to Hydra, or copy the text and paste it directly into your favority text editor.

Now save your text file into your ```/scratch/genomics/<username>/rnaseq/trinity/``` directory as ```trinity.job```.

* Now submit your job with the command: ```qsub trinity.job```

</p>
</details>

###Instructions for the interactive queue:
<details><summary>Instructions for the interactive queue</summary>
<p>

(2) Lets run your commands on the **interactive queue**:  

First check your path:

```$ pwd ```

Then request your **resources**: We will need at least 4 threaded nodes.  

```$ qrsh -pe mthread 4 ```
```$ cd /scratch/genomics/<username>/rnaseq/trinity```

Load the **module**: 

```$ module load bioinformatics/trinity/2.8.5 ```

Run the **job** **command**: 


``` 	
	$ Trinity --seqType fq \
      	--left ../data/RNA_Eye_1.fastq \
      	--right ../data/RNA_Eye_2.fastq \
      	--max_memory 24G --CPU 4 \
      	--output RNA_Eye.trinity \
      	--trimmomatic --full_cleanup 
``` 

</p>
</details>

Soon your transcriptome assembly will be finished!

```
Results of all tutorials can be found here:
/data/genomics/workshops/RNAseq/RNAseq_results.tar.gz
```