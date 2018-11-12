---
title: 'Erreur RC2104 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: 6ac1786e795c0c8ed57af2d341f43b8ba39229c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517817"
---
# <a name="resource-compiler-error-rc2104"></a>Erreur RC2104 du compilateur de ressources 

mot clé ou nom de clé non défini : clé

Le mot clé ou le nom de clé spécifié n'est pas défini.

Cette erreur est souvent due à une erreur typographique dans la définition de la ressource ou dans le fichier d'en-tête inclus. Elle peut aussi être liée à un fichier d'en-tête manquant.

Pour résoudre ce problème, recherchez le fichier d'en-tête qui doit contenir le mot clé ou le nom de clé défini et vérifiez qu'il est inclus dans votre fichier de ressources. Assurez-vous aussi que le mot clé ou le nom de clé est correctement orthographié. Si votre projet a été créé avec un en-tête précompilé et que vous le supprimez par la suite, assurez-vous que le fichier de ressources contient toujours les en-têtes nécessaires.

Pour vérifier les mots clés définis et les noms de clé dans votre fichier de ressources dans Visual Studio, ouvrez le **affichage des ressources** fenêtre, dans la barre de menus, choisissez **vue**, **affichage des ressources**— et Ouvrez le menu contextuel pour le fichier .rc, puis choisissez **symboles des ressources** pour afficher la liste des symboles définis. Pour modifier les en-têtes inclus, ouvrez le menu contextuel pour le fichier .rc et choisissez **Include des ressources**.

Si vous obtenez le message suivant :

```
undefined keyword or key name: MFT_STRING
```

ouvrez \MCL\MFC\Include\AfxRes.h et ajoutez cette directive include :

```
#include <winresrc.h>
```