---
title: Valeurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bef044535d2f5a5b337823b1798feaea48745d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106272"
---
# <a name="values"></a>Valeurs

**ANSI 3.1.2.5** Représentations et jeux de valeurs des différents types de nombres à virgule flottante

Le type **float** contient 32 bits : 1 pour le signe, 8 pour l’exposant et 23 pour la mantisse. Sa plage est +/- 3.4E38 avec au moins 7 chiffres de précision.

Le type **double** contient 64 bits : 1 pour le signe, 11 pour l’exposant et 52 pour la mantisse. Sa plage est +/- 1.7E308 avec au moins 15 chiffres de précision.

Le type **long double** contient 80 bits : 1 pour le signe, 15 pour l’exposant et 64 pour la mantisse. Sa plage est +/- 1.2E4932 avec au moins 19 chiffres de précision. Notez qu’avec le compilateur Microsoft C, la représentation du type **long double** est identique au type **double**.

## <a name="see-also"></a>Voir aussi

[Mathématiques à virgule flottante](../c-language/floating-point-math.md)