---
description: 'En savoir plus sur : conventions d’appel'
title: Conventions d’appel
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: bb5dab14e9d046b6ccee75a4fb37bd7b105902dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308651"
---
# <a name="calling-conventions"></a>Conventions d’appel

Le compilateur Visual C/C++ fournit diverses conventions pour appeler des fonctions internes et externes. La compréhension de ces différentes approches peut vous aider à déboguer votre programme et à lier votre code avec des routines en langage assembleur.

Les rubriques se rapportant à ce sujet expliquent les différences entre les conventions d’appel, la façon dont les arguments sont passés et la manière dont les valeurs sont retournées par les fonctions. Elles présentent également les appels de fonction naked, une fonctionnalité avancée qui vous permet d’écrire votre propre code de prologue et d’épilogue.

Pour plus d’informations sur les conventions d’appel pour les processeurs x64, consultez [Convention d’appel](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Rubriques de cette section

- [Réussite des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md) ( **`__cdecl`** , **`__stdcall`** , **`__fastcall`** et autres)

- [Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)

- [Utilisation d'appels de fonction naked pour écrire du code personnalisé de prologue/épilogue](../cpp/naked-function-calls.md)

- [Coprocesseur à virgule flottante et conventions d’appel](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Voir aussi

[Modificateurs spécifiques à Microsoft](../cpp/microsoft-specific-modifiers.md)
