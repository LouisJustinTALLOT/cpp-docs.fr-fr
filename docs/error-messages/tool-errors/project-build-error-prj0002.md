---
title: Erreur de génération PRJ0002 de projet | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e48130c17e04c2671395161452c9e66000047
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195713"
---
# <a name="project-build-error-prj0002"></a>Erreur de génération de projet PRJ0002

> résultat d’erreur retourné à partir de '*ligne de commande*».

Une commande, *ligne de commande*, ce qui a été formé à partir de l’entrée d’utilisateur dans le **Pages de propriétés** boîte de dialogue, retourné un code d’erreur, mais aucune information n’apparaît dans le **sortie** fenêtre .

La résolution de cette erreur dépend de l’outil a généré l’erreur. Pour MIDL, vous obtiendrez une idée de ce qui pose problème si/o (rediriger la sortie) est définie.

Un fichier de commandes, tel qu’une étape de génération personnalisée ou un événement de build, ce qui n’est pas d’information sur les conditions d’échec peut également être la raison de cette erreur.