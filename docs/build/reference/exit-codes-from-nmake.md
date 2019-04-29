---
title: Codes de sortie de NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 25ea4060e7b7a968b6a9da78f344e645c5d43a44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271463"
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

[Exécution de NMAKE](running-nmake.md)
