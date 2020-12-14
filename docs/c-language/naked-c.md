---
description: 'En savoir plus sur : Naked (C)'
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: 8d45371f71ccffda2c7505587f0942671d24b047
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257015"
---
# <a name="naked-c"></a>Naked (C)

**Spécifique à Microsoft**

L’attribut de classe de stockage naked est une extension spécifique à Microsoft pour le langage C. Le compilateur génère un code sans code de prologue ni d'épilogue pour les fonctions déclarées avec l'attribut de classe de stockage naked. Les fonctions naked sont utiles lorsque vous devez écrire vos propres séquences de code de prologue/épilogue à l'aide de code assembleur inline. Les fonctions naked sont utiles pour écrire des pilotes de périphériques virtuels.

Pour obtenir des informations spécifiques sur l'utilisation de l'attribut naked, consultez [Fonctions naked](../c-language/naked-functions.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Attributs du Storage-Class étendu C](../c-language/c-extended-storage-class-attributes.md)
