---
title: Erreur BSCMAKE BK1503 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16bf228804cb24f4fe7a2428dc581116d4cec91d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064661"
---
# <a name="bscmake-error-bk1503"></a>Erreur BSCMAKE BK1503

ne peut pas écrire dans le fichier 'nom_fichier' [ : raison]

BSCMAKE combine les fichiers .sbr générés pendant la compilation dans une base de données de navigateur. Si la base de données de navigateur qui en résulte dépasse 64 Mo, ou si le nombre de fichiers d’entrée (.sbr) dépasse 4092, cette erreur est émise.

Si le problème est causé par des fichiers .sbr supérieur à 4092, vous devez réduire le nombre de fichiers d’entrée. À partir de Visual Studio, cela est possible en [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) votre projet entier, puis effectuez une revérification sur une base de fichier par fichier.

Si le problème est causé par un fichier .bsc supérieur à 64 Mo, ce qui réduit le nombre de fichiers .sbr en tant qu’entrée diminue la taille du fichier .bsc obtenu. En outre, la quantité d’informations de consultation peut être réduite en utilisant les /Em (exclure les symboles de développé de Macro), /El (exclure les Variables locales) et/es (exclure des fichiers système).

## <a name="see-also"></a>Voir aussi

[Options BSCMAKE](../../build/reference/bscmake-options.md)