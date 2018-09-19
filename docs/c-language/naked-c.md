---
title: Naked (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6665bafb0041989e99a3a766204555f969d16c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062148"
---
# <a name="naked-c"></a>Naked (C)

**Section spécifique à Microsoft**

L’attribut de classe de stockage naked est une extension spécifique à Microsoft pour le langage C. Le compilateur génère un code sans code de prologue ni d'épilogue pour les fonctions déclarées avec l'attribut de classe de stockage naked. Les fonctions naked sont utiles lorsque vous devez écrire vos propres séquences de code de prologue/épilogue à l'aide de code assembleur inline. Les fonctions naked sont utiles pour écrire des pilotes de périphériques virtuels.

Pour obtenir des informations spécifiques sur l'utilisation de l'attribut naked, consultez [Fonctions naked](../c-language/naked-functions.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Attributs étendus de classe de stockage C](../c-language/c-extended-storage-class-attributes.md)