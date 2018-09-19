---
title: Formats date/heure Windows 32 bits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- vc.time
dev_langs:
- C++
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55eca447de7818f749628505a4c4f2fa6eb0dcd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061110"
---
# <a name="32-bit-windows-timedate-formats"></a>Formats date/heure Windows 32 bits

La date et l’heure du fichier sont stockées séparément, à l’aide d’entiers non signés utilisés comme des champs de bits. La date et l’heure du fichier sont empaquetées comme suit :

### <a name="time"></a>réflexion

|Position de bit :|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|
|-------------------|-----------------------|---------------------------|-----------------------|
|Longueur :|5|6|5|
|Contenu :|heures|minutes|incréments de 2 secondes|
|Plage de valeurs :|0-23|0-59|0-29 dans des intervalles de 2 secondes|

### <a name="date"></a>Date

|Position de bit :|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|
|-------------------|-------------------------------|-------------------|-----------------------|
|Longueur :|7|4|5|
|Contenu :|année|mois|jour|
|Plage de valeurs :|0-119|1-12|1-31|
||(par rapport à 1980)|||

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)