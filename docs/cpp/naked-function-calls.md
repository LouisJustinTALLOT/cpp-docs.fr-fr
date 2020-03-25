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
ms.openlocfilehash: 14bc64314cf64e7d13c076c314419e3d636432d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177935"
---
# <a name="naked-function-calls"></a>Appels de fonction naked

**Section spécifique de Microsoft**

Les fonctions déclarées avec l’attribut **Naked** sont émises sans code de prologue ou d’épilogue, ce qui vous permet d’écrire vos propres séquences de prologue/épilogue personnalisées à l’aide de l' [assembleur inline](../assembler/inline/inline-assembler.md). Les fonctions naked sont fournies en tant que fonctionnalité avancée. Elles vous permettent de déclarer une fonction appelée à partir d'un contexte autre que C/C++, et ainsi de faire des hypothèses différentes quant à l'emplacement où se trouvent les paramètres ou sur les registres qui sont conservés. Il s'agit par exemple de routines telles que les gestionnaires d'interruptions. Cette fonctionnalité est particulièrement utile pour les rédacteurs de pilotes de périphériques virtuels (VxDs).

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [naked](../cpp/naked-cpp.md)

- [Règles et limitations concernant les fonctions naked](../cpp/rules-and-limitations-for-naked-functions.md)

- [Considérations sur l’écriture de code de prologue/épilogue](../cpp/considerations-for-writing-prolog-epilog-code.md)

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
