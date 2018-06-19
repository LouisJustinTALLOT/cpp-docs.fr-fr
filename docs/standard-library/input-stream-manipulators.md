---
title: Manipulateurs de flux d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30f642dc4942491bd73265e3d647d3281f97c1e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842203"
---
# <a name="input-stream-manipulators"></a>Manipulateurs de flux d'entrée

Plusieurs manipulateurs, tel que [setprecision](../standard-library/iomanip-functions.md#setprecision), sont définis pour le `ios` de classe et par conséquent, s’appliquent pour les flux d’entrée. Quelques manipulateurs affectent néanmoins les objets de flux d’entrée proprement dits. Parmi eux, les plus importants sont les manipulateurs de base, `dec`, `oct` et `hex`, qui déterminent la base de conversion utilisée avec les nombres du flux d’entrée.

Lors de l’extraction, le manipulateur `hex` autorise le traitement de divers formats d’entrée. Par exemple, c, C, 0xc, 0xC, 0Xc et 0XC sont tous interprétés comme l’entier décimal 12. Tout caractère autre que ceux de 0 à 9, de A à F, de a à f, x et X mettent fin à la conversion numérique. Ainsi, la séquence `"124n5"` est convertie en nombre 124 avec le bit [basic_ios::fail](../standard-library/basic-ios-class.md#fail) défini.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)<br/>
