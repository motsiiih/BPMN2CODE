# BPMN2CODE
<img width="250px" src="https://user-images.githubusercontent.com/76916015/155765482-95393cab-49b6-4957-99a5-6807ca8cb207.png"/>
<br>
Tool that generates Python code starting from a BPMN model

## Introduction
I Multi-Robot Systems (MRSs) consistono in un gruppo di robot atti a cooperare al fine di eseguire una mission in maniera più efficiente di un Single-Robot System. Inoltre, i MRSs presentano caratteristiche vantaggiose come, ad esempio, una maggior affidabilità, versatilità e scalabilità, rispetto ai Single-Robot Systems. Sebbene esistano framework che facilitano il processo di programmazione e coordinazione dei robot che costituiscono un MRS, tale lavoro richiede comunque un alto livello di conoscenze ed abilità.
Questo progetto ha l’obiettivo di fornire un approccio ad alto livello alla modellazione dei comportamenti che i robot dovranno seguire, traducendo modelli realizzati seguendo lo standard BPMN 2.0 in linguaggio Python. La motivazione dietro la scelta di questo linguaggio è che esso è nativamente supportato da ROS (Robot Operating System), un framework che fornisce librerie e tool per semplificare la creazione di robot applications.
 In questo modo, è possibile applicare un approccio model-driven che parta dalla modellazione del comportamento di un robot alla traduzione del modello in codice eseguibile.
Il tool si inserirà nel contesto di un progetto più ampio nel quale si vuole dimostrare l’efficacia dello standard BPMN utilizzato nella modellazione di MRSs eseguita ad alto livello.

## Case Study
### BPMN model that describes the behaviour of an RC Car:
<img src="https://user-images.githubusercontent.com/76916015/155442289-b885dcca-ef1b-4275-84d3-4bb6e4a63893.png"/>

### Code generated by our tool:

```
from multiprocessing import Process

class Result:

 def runInParallel(*fns):
    proc = []
    for fn in fns:
      p = Process(target=fn)
      p.start()
      proc.append(p)
    for p in proc:
      p.join()


 if __name__ == '__main__':
    set_steps(10)
    while steps > 0: 
      check_distance()
      if distance > 30: 
        runInParallel(turn_on_led(), go_forward(20, distance))
        turn_off_led()
        decrease_steps(1)
      else: 
        decide_turn()
        if decision == 'left': 
          turn_left()
        else: 
          turn_right()
```
