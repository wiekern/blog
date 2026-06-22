---
title: Bereinigte Form
date: '2016-02-21T22:23:39+01:00'
categories: []
tags: []
description: Bereinigte Form erfüllt die folgenden Bedingungen,
---

Bereinigte Form erfüllt die folgenden Bedingungen,

1. Jede gebundene Variable in der Form wird unterschiedlich genannt.  
 z.B.  
$ \forall xP(x) \lor \forall xQ(x) $    ist keine bereinigte Form.  
$ \equiv \forall xP(x) \lor \forall yQ(y) $   gebundene UmbenennungQ(x)[x/y], bereinigte Form
2. Keine Variable in der Formel ist sowohl gebunden als auch frei.  
 z.B.  
$ \forall xP(x)  \lor Q(x) $ ist keine bereinigte Form.  
$\equiv \forall yP(y)  \lor Q(x) $ bereinigt  
**Achtung:** $\forall xP(x)  \lor Q(y)$ Das geht nicht. Denn bei der Bereinigung darf man nur die gebundene Variable umbenennen.

Jetzt nehmen wir noch ein Beispiel, das die obigen Eigenschaften besitzt.  
z.B.  
$ \forall xP(x) \lor Q(x) \lor \exists xQ(x) $ nicht bereinigt  
$ \equiv \forall xP(x) \lor Q(y) \lor \exists zQ(z) $ bereinigt

Bei der Aufgabe 32:  
(a) $ \forall x(P(x) \lor Q(a) \lor \exists xQ(x)) $  
$ \equiv \forall x(P(x) \lor Q(a) \lor \exists yQ(y)) $

(b) $ \forall x(P(x) \rightarrow \exists x(Q(x) \rightarrow \forall x(\forall x R(x) \rightarrow S(x)))) $  
$ \equiv \forall x(P(x) \rightarrow \exists y(Q(y) \rightarrow \forall z(\forall u R(u) \rightarrow S(z)))) $
