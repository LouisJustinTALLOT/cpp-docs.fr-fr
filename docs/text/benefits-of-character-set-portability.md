---
title: Avantages de la portabilité d'un jeu de caractères
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 0ca7e46cabb2d98a64a244863f8574a3e9e2a456
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410774"
---
# <a name="benefits-of-character-set-portability"></a>Avantages de la portabilité d'un jeu de caractères

Vous pouvez bénéficier de l’utilisation des fonctionnalités de portabilité runtime MFC et C même si vous ne comptez pas internationaliser votre application :

- Le codage portable rend votre code base flexible. Vous pouvez ultérieurement la déplacer facilement vers MBCS ou Unicode.

- L’utilisation d’Unicode rend vos applications Windows plus efficace. Étant donné que Windows utilise Unicode, les chaînes non-Unicode passés à et depuis le système d’exploitation doivent être traduites, ce qui entraîne une surcharge.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Prise en charge pour Unicode](../text/support-for-unicode.md)
