Implementing S.IM.PL : A Road Map 
=====

S.IM.PL is a relatively large software system; great pains have been taken to simplify it to the point that it is still easy to port and reimplement on many languages and platforms... additional work is being done to help make sure that simpl implementations are easy to validate and test. However, there still is some work to be done. 

You can tackle your implementation of S.IM.PL in a few different ways. You could imagine starting the entire system from scratch, writing description classes and proceding accordingly. That workflow will be described as one possibility. An additional way to make porting simpl more enjoyable can be accomplished by leveraging freshly-written translation infrastructure and boot-strapping the bulk of your implementation from this. 

No matter how you choose to implement simpl, you always should endeavor to keep it under test and make sure to double check your implementations against the baseline. Once you've implemented a minimal subset of simpl, it will become possible for you to test your S.IM.PL implementation against our S.IM.PL testing service; in effect, you'll be using your S.IM.PL validation to validate S.IM.PL. How cool is that?! Once you have more of your implementation tested, you'll be able to upload your implementation and take part in swarm testing of S.IM.PL.


To leverage the translation infrastructure as a jumpstart of your simpl port:
1. Fork the SimplJava repository. (At the moment, all of our translation code lives in our java repository; as Simpl becomes more prolifically used, you would imagine finding a repository that has some translators and writing a translator in that repository. For now; write your translator in java... if you can append things to a list in any language, you're all ready to write a translator.) 
2. Create a new directory named after your language. (If you feel like competing with someone else's implementation, name your folder language-yourname)
3. The entire translation infrastructure is designed to convert descriptions of data types into "source code entries." Source code entries are simply lines of code in a source file. The SourceCodeAppender allows you to automatically indent/unindent blocks of code (and also wrap blocks in braces) without additional work. To focus on making the mapping, look at some representations of a described data type in your language (or try rewriting bjects in one language in your language.) You'll naturally notice mappings between how fields are described to how they are written in your language! Simply write translators to capture all of these observations. Once you've written these, your translator should basically be complete! 
4. Test your translator with some preliminary runs, then run the translator on the SimplCore SimpltypesScope (included in simplTranslators) SimplCore contains the core of simpl, all of the description classes, the core implementations of the nterpretation framework, etc. If you've written your translator correctly, when you run SimplCore through the translator, you'll recieve a complete skeleton implementation of Simpl. 
5. If your skeleton looks correct, you could always send us a pull request so we can include your translator. :) 


Once you have written your translator, it is relatively straightforward to procde through simpl. 
If you are writing SIMPL in a language that is a "Source" language, you should first make sure that you can create descriptions from annotated classes. This will require parsing your classes (probably reflectively) to obtain type and annotation information. 

Once you have written the description layer (OR: As a "Target" Language, you can start here) , you can begin implementin the rest of simpl. I would procede thusly:

1. Write implementations of the core Scalar types. You should be ablet o map between strings and scalars easily.
2. Write the interpretation layer. 
3. Write your understanding layer.
4. Pick a string format (JSON is a nice start): Implement a serializer in this format
5. At this point, you can start to use SIMPL's test services to test your implementation...
6. Cover all cases of Simpl serialiation (you may need to translate additonal test classes) 
7. Implement the deserialization layer for your format. (That is, converting the format represntation to a list of interpretations.) 
8. Plug everything together and test round-trip serialization in your format. 
9. At this point, you can consider implementing more formats, as you wish 
10. Now that you can adequately serialize and deserialize simpl information, you can also implement the invocation layer. 
11. If you've gotten this far, run your simpl implementation against some of our other service-based testing sevices, and you're done! When you feel comfortable with your implementation, send us a link to your github repository and we'll gladly tell the world about it !

  
