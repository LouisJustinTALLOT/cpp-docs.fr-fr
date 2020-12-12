---
description: 'En savoir plus sur : manipulateurs de flux d’entrée'
title: Manipulateurs de flux d'entrée
ms.date: 11/04/2016
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
ms.openlocfilehash: 3da317a9e01652debe0114cfbde284ec0edf6db3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323987"
---
# <a name="input-stream-manipulators"></a>Manipulateurs de flux d'entrée

De nombreux manipulateurs, tels que [setprecision](../standard-library/iomanip-functions.md#setprecision), sont définis pour la `ios` classe et s’appliquent donc aux flux d’entrée. Quelques manipulateurs affectent néanmoins les objets de flux d’entrée proprement dits. Parmi eux, les plus importants sont les manipulateurs de base, `dec`, `oct` et `hex`, qui déterminent la base de conversion utilisée avec les nombres du flux d’entrée.

Lors de l’extraction, le manipulateur `hex` autorise le traitement de divers formats d’entrée. Par exemple, c, C, 0xc, 0xC, 0Xc et 0XC sont tous interprétés comme l’entier décimal 12. Tout caractère autre que ceux de 0 à 9, de A à F, de a à f, x et X mettent fin à la conversion numérique. Ainsi, la séquence `"124n5"` est convertie en nombre 124 avec le bit [basic_ios::fail](../standard-library/basic-ios-class.md#fail) défini.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)
