---
title: Erreur de génération PRJ0035 de projet | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0035
dev_langs:
- C++
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd36604763e28fc3f228adec27d0c3775a327d66
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213023"
---
# <a name="project-build-error-prj0035"></a>Erreur de génération de projet PRJ0035

> Fichier XML «*fichier*' contient du code Unicode qui n’a pas pu être traduit dans la page de code ANSI de l’utilisateur.
>
> *Contenu UNICODE du fichier*

*fichier* est le fichier XML créé en tant que la ligne de commande à l’outil de déploiement Web.

Le système de projet trouvé des caractères Unicode dans une propriété sur la page de propriétés de déploiement Web ne peut pas être traduite correctement en ANSI.

La résolution de cette erreur consiste à mettre à jour le contenu de la propriété à utiliser ANSI ou pour installer la page de codes sur votre ordinateur et définissez-la comme la valeur par défaut du système.