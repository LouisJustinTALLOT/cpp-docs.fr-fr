---
title: Erreur PRJ0008 de Build de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7c24634a845423de590228af01cb9f4779e37ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062785"
---
# <a name="project-build-error-prj0008"></a>Erreur de génération de projet PRJ0008

N’a pas pu supprimer le fichier 'fichier'.

**Assurez-vous que le fichier n’est pas ouvert par un autre processus et qu’il n’est pas protégé en écriture.**

Lors d’une reconstruction ou de nettoyage, Visual C++ supprime tous les fichiers intermédiaires et de sortie connus de la génération, ainsi que tous les fichiers qui répondent aux spécifications de caractères génériques dans le **Extensions à supprimer lors du nettoyage** propriété dans le [général Page de propriétés de paramètres de configuration](../../ide/general-property-page-project.md).

Vous verrez cette erreur si Visual C++ n’est pas en mesure de supprimer un fichier. Pour résoudre l’erreur, veillez au fichier et son répertoire accessible en écriture pour l’utilisateur qui effectue la build.