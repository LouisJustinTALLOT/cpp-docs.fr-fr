---
title: Varargs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8305eaddf87a2e67b797bedff1944dbcbbbdbd41
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713646"
---
# <a name="varargs"></a>Varargs

Si des paramètres sont passés par le biais de varargs (par exemple, les arguments de points de suspension), essentiellement le passage de paramètres normal s’applique, y compris le dépassement de la cinquième et ultérieures des arguments. Il incombe à nouveau l’appelé aux arguments de vidage qui ont leur adresse est acceptée. Pour les valeurs à virgule flottante, l’entier et le Registre à virgule flottante contiendra la valeur float si l’appelé attend la valeur dans les registres d’entiers.

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)