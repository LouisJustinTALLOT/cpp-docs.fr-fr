---
title: Avantages du caractère d’un jeu portabilité | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 115a4524f3b11d847291015f3bee5ca10f628310
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423440"
---
# <a name="benefits-of-character-set-portability"></a>Avantages de la portabilité d'un jeu de caractères

Vous pouvez bénéficier de l’utilisation des fonctionnalités de portabilité runtime MFC et C même si vous ne comptez pas internationaliser votre application :

- Le codage portable rend votre code base flexible. Vous pouvez ultérieurement la déplacer facilement vers MBCS ou Unicode.

- L’utilisation d’Unicode rend vos applications Windows plus efficace. Étant donné que Windows utilise Unicode, les chaînes non-Unicode passés à et depuis le système d’exploitation doivent être traduites, ce qui entraîne une surcharge.


## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Prise en charge pour Unicode](../text/support-for-unicode.md)