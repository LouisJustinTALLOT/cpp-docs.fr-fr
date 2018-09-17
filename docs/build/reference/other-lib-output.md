---
title: Autre sortie LIB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- output files, LIB
ms.assetid: 656864a6-0b7a-4633-8dc6-ee3b1766d836
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bd31c0534ae7ff2e7d840ad245be6f66983ea0a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704239"
---
# <a name="other-lib-output"></a>Autre sortie LIB

Dans le mode par défaut, vous pouvez utiliser l’option /LIST pour afficher des informations sur la bibliothèque qui en résulte. Vous pouvez rediriger cette sortie vers un fichier.

LIB affiche un message de copyright et la version et renvoie les fichiers de commandes, sauf si l’option /NOLOGO est utilisée.

Quand vous tapez `lib` avec aucune autre entrée, LIB affiche une instruction d’utilisation qui récapitule ses options.

Erreur et avertissement messages émis par LIB ont le format LNK*nnnn*. Les outils de lien, DUMPBIN et EDITBIN utilisent également cette plage d’erreurs. Aide est disponible en sélectionnant l’erreur dans la fenêtre Sortie et en appuyant sur F1.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de LIB](../../build/reference/overview-of-lib.md)