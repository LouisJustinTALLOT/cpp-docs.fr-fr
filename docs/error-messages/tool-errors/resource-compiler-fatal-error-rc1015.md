---
description: 'En savoir plus sur : erreur irrécupérable du compilateur de ressources RC1015'
title: 'Erreur irrécupérable RC1015 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC1015
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
ms.openlocfilehash: 41afe385189d35e80e5f624d379b45c0dca17441
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265660"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Erreur irrécupérable RC1015 du compilateur de ressources 

Impossible d’ouvrir le fichier include’nom_fichier'

Le fichier include spécifié n’existe pas, n’a pas pu être ouvert ou est introuvable.

Vérifiez que les paramètres d’environnement sont valides et que le chemin du fichier est spécifié et correct. Assurez-vous que suffisamment de handles de fichiers sont disponibles pour le compilateur de ressources. Si le fichier se trouve sur un lecteur réseau, assurez-vous que vous disposez des autorisations nécessaires pour ouvrir le fichier.

RC1015 peut se produire même si le fichier include existe dans un répertoire spécifié en tant que répertoire include supplémentaire dans la page de propriétés configuration-ressources->-> de propriétés générales ; Spécifiez le chemin d’accès complet au fichier include.
