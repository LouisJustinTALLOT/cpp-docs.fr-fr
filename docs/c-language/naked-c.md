---
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: 519d7bceb700e9862f0d0025b755cf28fb0fbc0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325778"
---
# <a name="naked-c"></a>Naked (C)

**Spécifique à Microsoft**

L’attribut de classe de stockage naked est une extension spécifique à Microsoft pour le langage C. Le compilateur génère un code sans code de prologue ni d'épilogue pour les fonctions déclarées avec l'attribut de classe de stockage naked. Les fonctions naked sont utiles lorsque vous devez écrire vos propres séquences de code de prologue/épilogue à l'aide de code assembleur inline. Les fonctions naked sont utiles pour écrire des pilotes de périphériques virtuels.

Pour obtenir des informations spécifiques sur l'utilisation de l'attribut naked, consultez [Fonctions naked](../c-language/naked-functions.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Attributs étendus de classe de stockage C](../c-language/c-extended-storage-class-attributes.md)
