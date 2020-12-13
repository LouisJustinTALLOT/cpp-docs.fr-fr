---
description: 'En savoir plus sur : avantages de la portabilité des jeux de caractères'
title: Avantages de la portabilité d'un jeu de caractères
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 32d78e6a230d664970e819f766d70beb1df52a88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187622"
---
# <a name="benefits-of-character-set-portability"></a>Avantages de la portabilité d'un jeu de caractères

Vous pouvez tirer parti de l’utilisation des fonctionnalités de portabilité MFC et Runtime C, même si vous n’envisagez pas d’internationaliser votre application :

- Le codage portable rend votre code flexible. Vous pouvez ultérieurement le déplacer facilement vers Unicode ou MBCS.

- L’utilisation d’Unicode rend vos applications plus efficaces pour Windows. Étant donné que Windows utilise Unicode, les chaînes non-Unicode transmises depuis et vers le système d’exploitation doivent être traduites, ce qui entraîne une surcharge.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Prise en charge pour Unicode](../text/support-for-unicode.md)
