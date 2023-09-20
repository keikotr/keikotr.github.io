---
layout: essay
type: essay
title: "Is it Smart to Ask?"
# All dates must be YYYY-MM-DD format!
date: 2023-09-07
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/smartquestion.jpg">

## Are you asking questions? Or are you asking nothing?

During all my years of schooling, there was one consistent phrase that all my teachers would say at the beginning of classes, "Please hold your questions until after the lesson because I may answer your question with the lesson!" More often than not, a student would ask a question in the middle of the lesson and the teacher would respond with, "Please wait a moment, I am about to answer that with the lesson." or "Please do not ask those kinds of questions, I have no appropriate answer to it." So was the student asking a question in a smart way? Or was the student asking questions in a not-so-smart way? Half of us may say that the student had a smart question but asked at the wrong time and topic, while the other half of us may say that the student was asking obscure questions that had zero relevance to the topic! Let me take you to some real examples found on Stack Overflow.

## What is a smart question?

What is Stack Overflow you may ask? Stack Overflow is an online forum for programmers to ask questions about anything tech-related! It is a great resource for those who are struggling to resolve a bug in their program or want to be introduced to other people's perspectives on different methods of doing something. I have found both good and bad questions on Stack Overflow to highlight the ups and downs of both questions.

In the following is an example of a <a href="https://stackoverflow.com/questions/11227809/why-is-processing-a-sorted-array-faster-than-processing-an-unsorted-array">good question</a> that follows asking questions in a smart way:

```
Q: Why is processing a sorted array faster than processing an unsorted array?

In this C++ code, sorting the data (before the timed region) makes the primary loop ~6x faster:

#include <algorithm>
#include <ctime>
#include <iostream>

int main()
{
    // Generate data
    const unsigned arraySize = 32768;
    int data[arraySize];

    for (unsigned c = 0; c < arraySize; ++c)
        data[c] = std::rand() % 256;

    // !!! With this, the next loop runs faster.
    std::sort(data, data + arraySize);

    // Test
    clock_t start = clock();
    long long sum = 0;
    for (unsigned i = 0; i < 100000; ++i)
    {
        for (unsigned c = 0; c < arraySize; ++c)
        {   // Primary loop.
            if (data[c] >= 128)
                sum += data[c];
        }
    }

    double elapsedTime = static_cast<double>(clock()-start) / CLOCKS_PER_SEC;

    std::cout << elapsedTime << '\n';
    std::cout << "sum = " << sum << '\n';
}

- Without std::sort(data, data + arraySize);, the code runs in 11.54 seconds.
- With the sorted data, the code runs in 1.93 seconds.
(Sorting itself takes more time than this one pass over the array, so it's not actually worth doing if we needed to calculate this for an unknown array.)

Initially, I thought this might be just a language or compiler anomaly, so I tried Java:
import java.util.Random;

public class Main
{
    public static void main(String[] args)
    {
        // Generate data
        int arraySize = 32768;
        int data[] = new int[arraySize];

        Random rnd = new Random(0);
        for (int c = 0; c < arraySize; ++c)
            data[c] = rnd.nextInt() % 256;

        // !!! With this, the next loop runs faster
        Arrays.sort(data);

        // Test
        long start = System.nanoTime();
        long sum = 0;
        for (int i = 0; i < 100000; ++i)
        {
            for (int c = 0; c < arraySize; ++c)
            {   // Primary loop.
                if (data[c] >= 128)
                    sum += data[c];
            }
        }

        System.out.println((System.nanoTime() - start) / 1000000000.0);
        System.out.println("sum = " + sum);
    }
}

With a similar but less extreme result.

My first thought was that sorting brings the data into the cache, but that's silly because the array was just generated.

What is going on?
Why is processing a sorted array faster than processing an unsorted array?
The code is summing up some independent terms, so the order should not matter.

```
The reason why this question is a smart question is because amount of details the original poster included. The original poster included their source code, specifying what language they used, and then explained their testing process, including the results they got. The amount of details that were included in the question allows people reading to replicate it at home as if it were an experiment done by a scientist. People looking to respond can also understand specifically what kind of answer the original poster is looking for because of how clear and concise the poster made it. Overall, this question was a good question since it was too specific to get a simple Google search, so using the poster asked a good question using the correct category tags.

While this question failed to include what operating system they were using, they had included what language they were coding in so people who are looking to replicate it for themselves can have the blueprint of what the poster exactly did which in turn, we can overlook the failure to include the operating system used. 

The answers provided by the community also demonstrate that the question was asked in a smart way. The top answer to the question was:

```
A: You are a victim of branch prediction fail.

What is Branch Prediction?
Consider a railroad junction:

Now for the sake of argument, suppose this is back in the 1800s - before long-distance or radio communication.

You are a blind operator of a junction and you hear a train coming. You have no idea which way it is supposed to go. You stop the train to ask the driver which direction they want. And then you set the switch appropriately. Trains are heavy and have a lot of inertia, so they take forever to start up and slow down.

Is there a better way? You guess which direction the train will go!
- If you guessed right, it continues on.
- If you guessed wrong, the driver will stop, back up, and yell at you to flip the switch. Then it can restart down the other path.
If you guess right every time, the train will never have to stop.
If you guess wrong too often, the train will spend a lot of time stopping, backing up, and restarting.

Consider an if-statement: At the processor level, it is a branch instruction:
You are a processor and you see a branch. You have no idea which way it will go. What do you do? You halt execution and wait until the previous instructions are complete. Then you continue down the correct path. Modern processors are complicated and have long pipelines. This means they take forever to "warm up" and "slow down".

Is there a better way? You guess which direction the branch will go!
- If you guessed right, you continue executing.
- If you guessed wrong, you need to flush the pipeline and roll back to the branch. Then you can restart down the other path.
If you guess right every time, the execution will never have to stop.
If you guess wrong too often, you spend a lot of time stalling, rolling back, and restarting.

This is branch prediction. I admit it's not the best analogy since the train could just signal the direction with a flag. But in computers, the processor doesn't know which direction a branch will go until the last moment.

How would you strategically guess to minimize the number of times that the train must back up and go down the other path? You look at the past history! If the train goes left 99% of the time, then you guess left. If it alternates, then you alternate your guesses. If it goes one way every three times, you guess the same...

In other words, you try to identify a pattern and follow it. This is more or less how branch predictors work.

Most applications have well-behaved branches. Therefore, modern branch predictors will typically achieve >90% hit rates. But when faced with unpredictable branches with no recognizable patterns, branch predictors are virtually useless. Further reading: "Branch predictor" article on Wikipedia.

As hinted from above, the culprit is this if-statement:
if (data[c] >= 128)
    sum += data[c];
Notice that the data is evenly distributed between 0 and 255. When the data is sorted, roughly the first half of the iterations will not enter the if-statement. After that, they will all enter the if-statement.

This is very friendly to the branch predictor since the branch consecutively goes the same direction many times. Even a simple saturating counter will correctly predict the branch except for the few iterations after it switches direction.

Quick visualization:

T = branch taken
N = branch not taken

data[] = 0, 1, 2, 3, 4, ... 126, 127, 128, 129, 130, ... 250, 251, 252, ...
branch = N  N  N  N  N  ...   N    N    T    T    T  ...   T    T    T  ...

       = NNNNNNNNNNNN ... NNNNNNNTTTTTTTTT ... TTTTTTTTTT  (easy to predict)

However, when the data is completely random, the branch predictor is rendered useless, because it can't predict random data. Thus there will probably be around 50% misprediction (no better than random guessing).

data[] = 226, 185, 125, 158, 198, 144, 217, 79, 202, 118,  14, 150, 177, 182, ...
branch =   T,   T,   N,   T,   T,   T,   T,  N,   T,   N,   N,   T,   T,   T  ...

       = TTNTTTTNTNNTTT ...   (completely random - impossible to predict)

What can be done? If the compiler isn't able to optimize the branch into a conditional move, you can try some hacks if you are willing to sacrifice readability for performance.

Replace:
if (data[c] >= 128)
    sum += data[c];

with:
int t = (data[c] - 128) >> 31;
sum += ~t & data[c];
This eliminates the branch and replaces it with some bitwise operations.
(Note that this hack is not strictly equivalent to the original if-statement. But in this case, it's valid for all the input values of data[].)

Benchmarks: Core i7 920 @ 3.5 GHz

C++ - Visual Studio 2010 - x64 Release                Java - NetBeans 7.1.1 JDK 7 - x64
                
Scenario	                  Time (seconds)            Scenario	                Time (seconds)
Branching - Random data	    11.777                    Branching - Random data	  10.93293813
Branching - Sorted data	    2.352                     Branching - Sorted data	  5.643797077
Branchless - Random data	  2.564                     Branchless - Random data	3.113581453
Branchless - Sorted data	  2.587                     Branchless - Sorted data	3.186068823

Observations:
With the Branch: There is a huge difference between the sorted and unsorted data.
With the Hack: There is no difference between sorted and unsorted data.
In the C++ case, the hack is actually a tad slower than with the branch when the data is sorted.
A general rule of thumb is to avoid data-dependent branching in critical loops (such as in this example).

Update:
- GCC 4.6.1 with -O3 or -ftree-vectorize on x64 is able to generate a conditional move, so there is no difference between the sorted and unsorted data - both are fast. (Or somewhat fast: for the already-sorted case, cmov can be slower especially if GCC puts it on the critical path instead of just add, especially on Intel before Broadwell where cmov has 2 cycle latency: gcc optimization flag -O3 makes code slower than -O2)
- VC++ 2010 is unable to generate conditional moves for this branch even under /Ox.
- Intel C++ Compiler (ICC) 11 does something miraculous. It interchanges the two loops, thereby hoisting the unpredictable branch to the outer loop. Not only is it immune to the mispredictions, it's also twice as fast as whatever VC++ and GCC can generate! In other words, ICC took advantage of the test-loop to defeat the benchmark...
- If you give the Intel compiler the branchless code, it just outright vectorizes it... and is just as fast as with the branch (with the loop interchange).

This goes to show that even mature modern compilers can vary wildly in their ability to optimize code...
```

Not only did this answer successfully answer the question, but it also gave detailed reasoning to support their answer and updated accordingly as new information was discovered. This is a wonderful answer that indicates a question asked in a smart way!

## Why is no one answering my question?

Amongst the vast of questions posted on Stack Overflow, we find ourselves stumbling upon an obvious question that did not need to be asked on the forums and wish we could speak to the original poster to use Google instead because it would have taken the same amount of time as posting a question would!

The following is an example of a <a href="https://stackoverflow.com/questions/77062202/java-eclipse-data-transfer">question </a>that failed to be asked smartly:

```
Q: java eclipse data transfer

How would I be able to send info (a variable declared on the sender side) to another computer (recipient side) without compromising any of the recipients side's data including ip, or passwords if using an email approach.
```

The contents of this question are too vague and fail to provide any details on what they have already tried, any errors along the way, and their source code. There is also a lack of what "eclipse" really is. One of the commenters on the post was confused if it was the Eclipse IDE or the Eclipse platform. Too much missing information leads to the question being unanswerable and people would be making too many assumptions/guesses to try and help the poster.

## What does this say about smart questions?

In a desperate call for help, we often may forget to stop and think about the question before speaking. Without any structure or details to the question, the people we are asking for help become clueless and cannot provide their expertise to use. Therefore, we must ask questions in a smart way so we can receive the best answer!
