---
title: Appels de fonction naked
ms.date: 11/04/2016
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
ms.openlocfilehash: 9b49d34d7276d3c9260488f23d1821b9708d2481
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227320"
---
# <a name="naked-function-calls"></a>Appels de fonction naked

**Spécifique à Microsoft**

Les fonctions déclarées avec l' **`naked`** attribut sont émises sans code de prologue ou d’épilogue, ce qui vous permet d’écrire vos propres séquences de prologue/épilogue personnalisées à l’aide de l' [assembleur inline](../assembler/inline/inline-assembler.md). Les fonctions naked sont fournies en tant que fonctionnalité avancée. Elles vous permettent de déclarer une fonction appelée à partir d'un contexte autre que C/C++, et ainsi de faire des hypothèses différentes quant à l'emplacement où se trouvent les paramètres ou sur les registres qui sont conservés. Il s'agit par exemple de routines telles que les gestionnaires d'interruptions. Cette fonctionnalité est particulièrement utile pour les rédacteurs de pilotes de périphériques virtuels (VxDs).

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [naked](../cpp/naked-cpp.md)

- [Règles et limitations pour les fonctions Naked](../cpp/rules-and-limitations-for-naked-functions.md)

- [Considérations relatives à l’écriture de code de prologue/épilogue](../cpp/considerations-for-writing-prolog-epilog-code.md)

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
