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
ms.openlocfilehash: d016b95ea2a2d5d94b8db47a2d6c9d5cc577083f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064444"
---
# <a name="benefits-of-character-set-portability"></a>Avantages de la portabilité d'un jeu de caractères

Vous pouvez bénéficier de l’utilisation des fonctionnalités de portabilité runtime MFC et C même si vous ne comptez pas internationaliser votre application :

- Le codage portable rend votre code base flexible. Vous pouvez ultérieurement la déplacer facilement vers MBCS ou Unicode.

- L’utilisation d’Unicode rend vos applications Windows plus efficace. Étant donné que Windows utilise Unicode, les chaînes non-Unicode passés à et depuis le système d’exploitation doivent être traduites, ce qui entraîne une surcharge.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Prise en charge pour Unicode](../text/support-for-unicode.md)