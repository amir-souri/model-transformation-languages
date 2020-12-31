# Difference between subject performance in using programming languages. 


This analysis is based on: [Regina Hebig, Christoph Seidl, Thorsten Berger, John Kook Pedersen, Andrzej Wasowski: Model transformation languages under a magnifying glass: a controlled experiment with Xtend, ATL, and QVT. ESEC/SIGSOFT FSE 2018: 445-455](DOIs: https://doi.org/10.1145/3236024.3236046).  I summarize all the information needed here, but please consult the paper, if you need more information.

This experiment compared three transformation langaguages (ATL, QVT-O, and Xtend). Transformation languages are languages for implementing syntax transformations (used for transforming data, models, or programs). The treatment in the experiment is the *transformation language* (a, q, or x for short). They asked 3 random groups of students to solve 3 tasks in one of the languages. The first task, **Comprehend**, required understanding a transformation program.  The second task, **Change**, required changing a transformation program to accommodate a new requirement.  The third task, **Create**, required creating a transformation program. Clearly, the three tasks cannot be solved on the same program. Once a program has been understood (Comprehend) and changed (Change), creating it would become an exercise in memorizing, not in programming. So for the third task they change the subject program. We use two subject programs, one called *FM*, involving some manipulation of Feature Models, and one called *RE*, involving some manipulation of the Relational Model. The content of the programs is not important for the task.

Each data point collected in the experiment is thus then characterized by: task, language, and outcome. The task ranges over: ComprehendFM, ComprehendRE, ChangeFM, ChangeRE, CreateFM, and CreateRE (thus two pieces of information, the task and the model are combined in this single column).  The language ranges over a, q, and x. The outcome is a value between 0 and 1 (percentage of points obtained after grading the subject solution by experts for correctness).  We do not know which rows originate from the same subjects, but the experiment design largely accounts for this before analysis -- the so called between-subjects design with cross-over (See section 4.1 in the paper if you are interested).  The data is distributed in the file (./model-transformation-languages.csv).

The paper formulates hypothesis in Section 4.3:

**H1** Subjects comprehending a QVT-O or Xtend transformation perform better than those who comprehend a transformation in ATL.

**H1_0** : Subjects comprehending a QVT-O or Xtend transformation perform worse or equal to those comprehending an ATL transformation.

**H2**: Subjects who change a transformation written in QVT-O or Xtend perform better than those who change a transformation in ATL.

**H2_0**: Subjects changeing a transformation written in QVT-O or Xtend perform worse or equal to those who change an ATL transformation.

**H3**: Subjects who create a model transformation in QVT-O or Xtend perform better than those who create a transformation in ATL.

**H3_0**: Subjects who create a model transformation in QVT-O or Xtend perform worse or equal to those who create a transformation in ATL.

**H4**: Subjects who comprehend a transformation in QVT-O perform better than those comprehending a transformation in Xtend.

**H4_0** : Subjects who comprehend a transformation written in QVT-O perform worse or equal to those comprehending it in Xtend.

**H5**: Subjects changing a transformation written in QVT-O perform better than the subjects who change an Xtend transformation.

**H5_0**: Subjects changing a transformation in QVT-O perform worse or equal than the subjects who change an Xtend transformation.

**H6**: Subjects who create a model transformation in QVT-O perform better than those who create a transformation in Xtend.

**H6_0**: Subjects who create a model transformation in QVT-O perform worse or equal to those who create a transformation in Xtend.

The paper uses standard frequentist statistics to analyze these data and it reports, pretty much a negative, result that there is no added benefit of using a more specialized language, like ATL, over the other two (that represent more standard languages).



The task is to uses Bayesian Inference and Bayesion Decision making to decide wether these hypothesis holds, or possibly reject them. This includes:

* Loading and cleaning the data (some entries have empty values for the performance/outcome column.  This means that a result is not available, and the row should be ignored)

* Design tests for hypotheses in pyMC3 comparing the languages.

* Check the quality of the sampling process and comment whether the quality is good.
