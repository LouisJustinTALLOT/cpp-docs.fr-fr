---
description: 'En savoir plus sur : les appels de fonction Naked'
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
ms.openlocfilehash: ffc28b65a8c16881164805f0cfa55ffe1bc54e9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313799"
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
