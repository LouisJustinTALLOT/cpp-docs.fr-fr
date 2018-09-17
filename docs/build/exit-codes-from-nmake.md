---
title: Codes de sortie de NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b5a593e38efb5230630ed01e65f4bfb1f2ba92a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722616"
---
# <a name="exit-codes-from-nmake"></a>Codes de sortie de NMAKE

NMAKE retourne les codes de sortie suivant :

|Code|Signification|
|----------|-------------|
|0|Aucune erreur (probablement un avertissement)|
|1|Génération incomplète (émise uniquement lorsque l’option /K est utilisé)|
|2|Erreur de programme, probablement en raison d’une des opérations suivantes :|
||-Une erreur de syntaxe dans le makefile|
||-Un erreur ou code de sortie à partir d’une commande|
||-Une interruption par l’utilisateur|
|4|Erreur système : mémoire insuffisante|
|255|Cible n’est pas à jour (émis uniquement lorsque l’option /Q est utilisé)|

## <a name="see-also"></a>Voir aussi

[Exécution de NMAKE](../build/running-nmake.md)