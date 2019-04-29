---
title: Erreur de génération de projet PRJ0002
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: d8e13bcc03a02fd9dbc739566a92025a7b97d598
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359707"
---
# <a name="project-build-error-prj0002"></a>Erreur de génération de projet PRJ0002

> résultat d’erreur retourné à partir de '*ligne de commande*».

Une commande, *ligne de commande*, ce qui a été formé à partir de l’entrée d’utilisateur dans le **Pages de propriétés** boîte de dialogue, retourné un code d’erreur, mais aucune information n’apparaît dans le **sortie** fenêtre .

La résolution de cette erreur dépend de l’outil a généré l’erreur. Pour MIDL, vous obtiendrez une idée de ce qui pose problème si/o (rediriger la sortie) est définie.

Un fichier de commandes, tel qu’une étape de génération personnalisée ou un événement de build, ce qui n’est pas d’information sur les conditions d’échec peut également être la raison de cette erreur.