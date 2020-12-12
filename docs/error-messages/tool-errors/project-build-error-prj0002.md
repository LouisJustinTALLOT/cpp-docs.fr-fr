---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0002'
title: Erreur de génération de projet PRJ0002
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: b9f3d06a71183902c92102f12f665decdbf35a9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119419"
---
# <a name="project-build-error-prj0002"></a>Erreur de génération de projet PRJ0002

> résultat d’erreur retourné à partir de la *ligne de commande*.

Une commande, *ligne de commande*, qui a été formée à partir d’une entrée d’utilisateur dans la boîte de dialogue **pages de propriétés** , a retourné un code d’erreur, mais aucune information n’apparaît dans la fenêtre **sortie** .

La résolution de cette erreur dépend de l’outil qui a généré l’erreur. Pour MIDL, vous allez avoir une idée de ce qui s’est produit si/o (sortie de redirection) est défini.

Un fichier de commandes, tel qu’une étape de génération personnalisée ou un événement de build, qui n’est pas informatif sur les conditions d’échec peut également être la raison de cette erreur.
