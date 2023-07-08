---
layout: post
title: Introduction to Logic
date: 2018-09-08
description: some basics of propositional logic
permalink: /blog/intro-to-logic
toc:
  sidebar: left
thumbnail: assets/img/header_logicintro.jpg
categories: MSLIS
---

A big part of learning basic logic is learning the terminology - and more specifically, learning what these words mean within the logical language (vs their typical English meanings). So I'm going to start this with a basic introduction of terms.

## Basic Definitions

**Logic** is the study of arguments: essentially, which statements follow from which, and why certain arguments are good or bad.

Generally, a logical argument will follow this format:

> Argument **A**  
**P**remise **1**: (statement)  
**P**remise **2**: (statement)  
**C**onclusion: (statement)  

**Statements** are:

 - the basic units of logic.
 - declarative sentences (not questions or suggestions)
 - either True OR False (not both, not neither)
 - not concerned with possibility, only logical truth/possibility.
    - For example, "I can go faster than light" is logically possible, even though it is physically impossible. "I am both in Illinois and not in Illinois" is not logically possible.

**Arguments** are:

 - also called propositions
 - groups of statements/claims
 - composed of 2 types of statements:
    - the *premises* (minimum of 1, but usually at least 2 in an argument)
    - the *conclusion* (1 per argument)

**Premises** are:

 - the statements that bear the evidence & provide support
 - NOTE: the premises might not actually support the conclusion, nor must premises be true/correct

**Conclusions** are:

 - the statement that is claimed to be supported by the premises
 - usually stated last in an argument (but could be first)
 - indicated in English by words/phrases like:
   - therefore, so, hence, consequently, entails, whence, thus, implies, whereby, as a result, if follows that, & we may infer

## Validity

Validity is a property of arguments (whereas truth is a property of statements).

If the conclusion of an argument follows from its premises, then the argument is said to be logically valid. (Otherwise, it's invalid)

### Technical definition of validity

Argument **A** is _valid_ if and only if:

- It is logically necessary that:
    1. If all of the *premises* of **A** are true, then the *conclusion* of **A** is also true

- It is logically impossible for both of the following to be true simultaneously:
    1. all *premises* of **A** are true
    2. *conclusion* of **A** is false

Note: these two statements are interchangeable - if an argument meets either of these requirements, it is valid.

### Truth Table for showing validity

| Premises | Conclusion | Valid? |
|--------|-------|--------|
| True   | True   | Yes   |
| True   | False   | No   |
|-----------------------------|
| False   | True   | Yes   |
| False   | False   | Yes   |

### Examples to demonstrate validity

> Argument **A**:  
**P1**: I am reading a book.  
**P2**: If I am reading a book, then I am happy.  
**C**: I am happy.  

Argument **A** is valid.  

> Argument **B**:  
**P1**: I have blue eyes.  
**P2**: Everyone who has blue eyes also has brown hair.  
**C**: I do not have brown hair.  

Argument **B** is not valid.  

> Argument **C**:  
**P1**: Zebras have stripes.  
**P2**: Lions eat zebras.  
**C**: Lions have manes.  

Argument **C** is not valid.  

> Argument **D**  
**P1**: The sun rose today.  
**P2**: The sun rose yesterday.  
**P3**: The sun has risen every day for the past billion years.  
**C**: The sun will rise tomorrow.  

Argument **D** is not valid, because it is conceivable that there could exist a world in which the premises are true while the conclusion is not. It doesn't matter that the conclusion is very likely... it is possible that it is not true (while the premises are true), therefore the whole argument is invalid (no matter how convincing it may seem).

Good arguments are valid, but validity is not enough for an argument to be good. You should also look at its soundness.

## Soundness

An argument is sound if (1) it is valid and (2) it has true premises. This means that *sound arguments have true conclusions*. Valid arguments can still have false conclusions, if the premises are false. And just because an argument has true premises and true conclusions, doesn't mean it is sound. It has to be a valid argument to be considered sound.

### Technical definition of soundness

Argument A is sound if and only if both:

 1. A is valid
 2. All of A’s premises are true

### Truth Table for showing soudness

| Premises | Conclusion | Valid? | Sound? |
|--------|-------|--------|--------|
| True   | True   | Yes   | Yes   |
| True   | False   | No   | No   |
|-----------------------------|
| False   | True   | Yes   | No   |
| False   | False   | Yes   | No   |

### Limits to soundness

Even sound arguments may not be good arguments. For example, this is a perfectly sound argument (in which the premise entails the conclusion):

> **P1**: Illinois is in the US.  
**C**: Illinois is in the US.

Valid? Yes. True premises & conclusions? Yes. Sound? Yes.   
Good? ... not so much.

## Some famous arguments (valid & invalid)

> Modus Ponens (Valid)  
**P1**: p  
**P2**: If p then q  
**C**: q  

> Modus Tollens (Valid)  
**P1**: Not q  
**P2**: If p then q  
**C**: Not p  

> Affirming the Consequent (Invalid)  
**P1**: q  
**P2**: If p then q  
**C**: p  

For the above 3 examples, think of two concentric circles, with p as the smaller circle inside q.

> Denying the Antecedent (Invalid)  
**P1**: Not p  
**P2**: If p then q  
**C**: Not q  

> Hypothetical Syllogism (Valid)  
**P1**: If p then q  
**P2**: If q then r  
**C**: If p then r  

> Disjunctive Syllogism (Valid)  
**P1**: Not p  
**P2**: Either p or q  
**C**: q  

For the above example, think of two intersecting circles of p and q (like a Venn diagram).

These examples are important, because they are proven to be valid or invalid. For formal validity, only arguments that take the form of a formally proven valid argument are considered valid. Absolute validity is a bit more relaxed, but for formal validity you must know the accepted (valid) forms.

### 2 weird but valid forms

> (**A**)  
**P1**: p  
**C**: q or not q  

> (**B**)  
**P1**: p and not p  
**C**: q  

**A** is valid simply because (**C**) “q or not q” is a logical truth. It’s impossible for the premise to be true and the conclusion false, since the conclusion is always true.

**B** is valid because “p and not p” is a logical falsehood. So it’s impossible that both (**P1**) “p and not p” is true and (**C**) q is false. That’s because (**P1**) is impossible.

If this is confusing (which it probably is), refer back to the official definition of validity:

 - It is logically necessary that if all the premises of A are true, then the conclusion of A is also true
 - It is logically impossible for both of the following to be true simultaneously: (1) all premises of A are true (2) the conclusion of A is false

## Sentential form

The sentential form of an argument is obtained by replacing each basic (atomic) sentence in the argument with a single (lower case) letter.

 - Basic sentences are sentences that don’t have any other sentence as a part.
 - Look for these words to indicate that the sentence is not atomic: and, but, not, either, or, nor
 - Sentences that are not basic/atomic are called complex/compound/molecular sentences.

When translating to sentential form, it is important to be as precise (fine-grained) as possible, and capture the closest meaning to the original English sentence as possible. This requires understanding the English very well. You should always capture all of the symbols you can from the sentence (and, or, not, if) in order to reduce the sentences down to their atomic form.

### The importance of being explicit

In order for an argument to be considered valid by strict logicians, you need to define your terms.

For example,

> Argument **A**  
**P1**: John is a bachelor.  
**C**: John is unmarried.

This seems true, but is it valid? Logicians say no. You need to add one more premise to the argument:

> Argument **B**  
**P1**: John is a bachelor.  
**P2**: All bachelors are unmarried.  
**C**: John is unmarried.  

Argument B is explicit. Argument A includes an implied definition, but does not explicitly define the term "bachelor." This occurs all of the time in English, which is why in logic we reduce statements to their sentential form. In sentential form, **A** is: b, therefore u. Clearly, this is invalid.

### Limits to sentential form

Sentential form cannot always capture validity - not all valid arguments have sentential forms. Higher orders of logic are needed to capture certain statements.

Syllogistic logic is an intermediate form of logic that can capture arguments like **B**. We could rewrite P2 in B to be "If John is a bachelor, then John is unmarried" to write it in sentential form: b -> u. However, written as "All bachelors are unmarried," we cannot write it in sentential form.

The classic example of a syllogism is:

>All men are mortal.  
Socrates is a man.  
Therefore, Socrates is mortal.  

### The Syntax of LSL (Language of Sentential Logic)

LSL is a formal language and has special symbols.

- Upper case letters symbolize atomic sentences
- Connectives (or operators) are special symbols that put sentences together
- parentheses group sentences together

The connectives/operators of LSL are:

 - not: ~ or ¬
 - and: & or ∧
 - or: ∨
 - if… then, only if: →
 - if and only if, iff: ↔

### 5 kinds of non-basic LSL sentences

- *conjunctions*: p ∧ q (where p, q are the conjuncts)
- *disjunctions*: p ∨ q (where p, q are the disjuncts)
- *conditionals*: p → q (where p is the antecedent and q is the consequent
- *biconditionals*: p ↔ q (where p is the left-hand side, and q is the right-hand side)
- *negations*: ¬p (where p is the negated sentence)


## In Conclusion

There we go! The basics of zeroth order propositional logic. The most important concept here is validity, and sentential form is just a tool we use to better capture an arguments validity (or invalidity).

Credits: The information in this post was pulled from the first two weeks of my PHIL103 class at UIUC.
