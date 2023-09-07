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

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/rtfm.png">

## Are you asking questions? Or are you asking nothing?

I’ve had instructors address a whole class and say, “There’s no such thing as a stupid question.” I now know that is in fact not true because I’ve challenged the statement and received the appropriate dumb-stricken, annoyed look. There are definitely stupid questions, and along with that, usually unhelpful answers. Though we all might be guilty of being callous and making people victim to our poorly formed questions, there are steps we can take to ask smarter questions that hopefully don’t illicit the dreaded “rtfm” or “stfw” response.

During all my years of schooling, there was one consistent phrase that all my teachers would say at the beginning of classes, "Please hold your questions until after the lesson because I may answer your question with the lesson!" More often than not, a student would ask a question in the middle of the lesson and the teacher would respond with, "Please wait a moment, I am about to answer that with the lesson." or "Please do not ask those kinds of questions, I have no appropriate answer to it." So was the student asking a question in a smart way? Or was the student asking questions in a not-so-smart way? Half of us may say that the student had a smart question but asked at the wrong time and topic, while the other half of us may say that the student was asking obscure questions that had zero relevance to the topic! Let me take you into some real examples found on Stack Overflow.

## What’s a smart question?

What is Stack Overflow you may ask? Stack Overflow is an online forum for programmers to ask questions about anything tech related! Its a great resource for those who are struggling to resolve a bug in their program or wants to be introduced to other peoples perspectives on different methods of doing something. I have found both a good and bad question found on Stack Overflow to highlight the ups and downs of both questions.

In the following is an example of a good question that follows asking questions in a smart way:
https://stackoverflow.com/questions/11227809/why-is-processing-a-sorted-array-faster-than-processing-an-unsorted-array

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
The reason why this question is a smart question is because amount of details the original poster included. The original poster included their source code, specifying what language they used, and then explained their testing process, including the results they got. The amount of details that were included in the question allows people reading to replicate it at home as if it were an experiment done by a scientist. People looking to respond can also understand specifically what kind of answer the original poster is looking for because of how clear and concise the poster made it. While this question failed to include what operating system they were using, they had included what language they were coding in so people who are looking to replicate it for themselves can have the blueprint of what the poster exactly did which in turn, we can overlook the failure to include the operating system used.

```
A: datetime and the datetime.timedelta classes are your friend.

1. find today
2. use that to find the first day of this month.
3. use timedelta to backup a single day, to the last day of the previous month.
4. print the YYYYMM string you're looking for.

Like this:

 >>> import datetime
 >>> today = datetime.date.today()
 >>> first = datetime.date(day=1, month=today.month, year=today.year)
 >>> lastMonth = first - datetime.timedelta(days=1)
 >>> print lastMonth.strftime("%Y%m")
 201202
 >>>

```
 
The asker received six possible answers, and he or she was successful in inciting discussion from multiple users. The answers themselves were clear and were devoid of the rumored sarcasm and hostility of “hackers.” Since I myself have referenced this page and found it useful, I can confidently say that it is a good question.

## The foolproof way to get ignored.

While there are decent questions that benefit everyone, there are those one can ask to create an entirely different effect. In the following example, a user asks how he would, in short, create a desktop application with Facebook.

```
Q: Facebook Desktop Notifier

I am a beginner programmer that have never used anything other than what's included in a language.

I am trying to create a desktop application that notifies me anytime I get an update onfacebook. 
How should go about doing this? Thanks in advance.

edit Sorry I was not clear. Is there any way to make a DESKTOP application with facebook?
```

A simple “yes” would have answered the question, but we know that’s not the sort of answer he or she is looking for. Fortunately, someone kindly responded with a link to Facebook’s developer website. The asker should have done more research on his or her potential project. Then further down the road, he or she could have asked more specific and detailed questions that wouldn’t require a thousand-paged response for a sufficient answer.

## Conclusion

When we rely on others’ generosity and expertise to provide answers to our questions, it should hold that the question we ask should be one that leads to efficient and effective help that not only benefits us, but also the people we ask and others who might ask the same question in the future. Thus, if you have a question… make it a smart one! Asking questions may not always get you the best answer, but asking them in a way that will make others want to answer them will increase the success of finding a good solution and make it a positive experience on all sides.
