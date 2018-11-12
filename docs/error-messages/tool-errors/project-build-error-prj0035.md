---
title: Erreur de génération de projet PRJ0035
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: e221fd85f1260ed04d49b43dea3d13407f504847
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472343"
---
# <a name="project-build-error-prj0035"></a>Erreur de génération de projet PRJ0035

> Fichier XML «*fichier*' contient du code Unicode qui n’a pas pu être traduit dans la page de code ANSI de l’utilisateur.
>
> *Contenu UNICODE du fichier*

*fichier* est le fichier XML créé en tant que la ligne de commande à l’outil de déploiement Web.

Le système de projet trouvé des caractères Unicode dans une propriété sur la page de propriétés de déploiement Web ne peut pas être traduite correctement en ANSI.

La résolution de cette erreur consiste à mettre à jour le contenu de la propriété à utiliser ANSI ou pour installer la page de codes sur votre ordinateur et définissez-la comme la valeur par défaut du système.