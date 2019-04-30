---
title: Manipulateurs de flux d'entrée
ms.date: 11/04/2016
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
ms.openlocfilehash: 17f18aa127b84538229b3cf4e4246dfefb6c1f98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404908"
---
# <a name="input-stream-manipulators"></a>Manipulateurs de flux d'entrée

Nombreux manipulateurs, tels que [setprecision](../standard-library/iomanip-functions.md#setprecision), sont définis pour le `ios` classe et s’appliquent donc aux flux d’entrée. Quelques manipulateurs affectent néanmoins les objets de flux d’entrée proprement dits. Parmi eux, les plus importants sont les manipulateurs de base, `dec`, `oct` et `hex`, qui déterminent la base de conversion utilisée avec les nombres du flux d’entrée.

Lors de l’extraction, le manipulateur `hex` autorise le traitement de divers formats d’entrée. Par exemple, c, C, 0xc, 0xC, 0Xc et 0XC sont tous interprétés comme l’entier décimal 12. Tout caractère autre que ceux de 0 à 9, de A à F, de a à f, x et X mettent fin à la conversion numérique. Ainsi, la séquence `"124n5"` est convertie en nombre 124 avec le bit [basic_ios::fail](../standard-library/basic-ios-class.md#fail) défini.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)<br/>
