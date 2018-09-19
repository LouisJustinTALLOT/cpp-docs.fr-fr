---
title: Signes de ponctuation (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 438b3f0469d1e8426b1e0ec2a19a63d1ae63c041
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039268"
---
# <a name="punctuators-c"></a>Signes de ponctuation (C++)

Les signes de ponctuation en langage C++ ont une signification syntaxique et sémantique pour le compilateur mais ne spécifient pas d'eux-mêmes une opération qui produit une valeur. Certains signes de ponctuation, seuls ou combinés, peuvent également être des opérateurs C++ ou être significatifs pour le préprocesseur.

Tous les caractères suivants sont considérés comme des signes de ponctuation :

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

Les signes de ponctuation **[]**, **()**, et **{}** doivent figurer par paires après [phase de traduction](../preprocessor/phases-of-translation.md) 4.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](../cpp/lexical-conventions.md)