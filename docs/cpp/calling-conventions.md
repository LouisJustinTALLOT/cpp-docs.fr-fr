---
title: Conventions d’appel
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: 432cb1b6910db5ea735288edfbf6aa9e10f0a486
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190285"
---
# <a name="calling-conventions"></a>Conventions d’appel

Le compilateur Visual C/C++ fournit diverses conventions pour appeler des fonctions internes et externes. La compréhension de ces différentes approches peut vous aider à déboguer votre programme et à lier votre code avec des routines en langage assembleur.

Les rubriques se rapportant à ce sujet expliquent les différences entre les conventions d’appel, la façon dont les arguments sont passés et la manière dont les valeurs sont retournées par les fonctions. Elles présentent également les appels de fonction naked, une fonctionnalité avancée qui vous permet d’écrire votre propre code de prologue et d’épilogue.

Pour plus d’informations sur les conventions d’appel pour les processeurs x64, consultez [Convention d’appel](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Rubriques de cette section

- [Réussite des arguments et conventions de nommage](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`et autres)

- [Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)

- [Utilisation d’appels de fonction Naked pour écrire du code de prologue/épilogue personnalisé](../cpp/naked-function-calls.md)

- [Coprocesseur à virgule flottante et conventions d’appel](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Voir aussi

[Modificateurs propres à Microsoft](../cpp/microsoft-specific-modifiers.md)
