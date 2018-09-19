---
title: Erreur irrécupérable RC1015 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a72cba53ebe9a286ac2e7cbbf2c41b78f4e4e08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100760"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Erreur irrécupérable RC1015 du compilateur de ressources 

ne peut pas ouvrir le fichier 'nom_fichier' include

Le fichier include spécifié n’existe pas, n’a pas pu être ouvert. ou est introuvable.

Vérifiez que les paramètres d’environnement sont valides et que le chemin du fichier est spécifié et correct. Assurez-vous que les descripteurs de fichiers suffisantes sont disponibles pour le compilateur de ressources. Si le fichier se trouve sur un lecteur réseau, assurez-vous que vous disposez des autorisations pour ouvrir le fichier.

RC1015 peut se produire même si le fichier include existe dans un répertoire spécifié comme autre répertoire inclus dans les propriétés de Configuration -> ressources -> page de propriétés Général ; Spécifiez le chemin d’accès complet du fichier include.

Pour plus d’informations, consultez l’article de la Base de connaissances Q326987 : RC1015 erreur quand à l’aide de ressources vue si le chemin d’accès Include est trop Long.