---
description: 'En savoir plus sur : erreur du compilateur de ressources RC2104'
title: 'Erreur RC2104 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: 74f50088d15fcc86ebfc7000d8ee618c94464c63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259979"
---
# <a name="resource-compiler-error-rc2104"></a>Erreur RC2104 du compilateur de ressources 

mot clé ou nom de clé non défini : clé

Le mot clé ou le nom de clé spécifié n'est pas défini.

Cette erreur est souvent due à une erreur typographique dans la définition de la ressource ou dans le fichier d'en-tête inclus. Elle peut aussi être liée à un fichier d'en-tête manquant.

Pour résoudre ce problème, recherchez le fichier d'en-tête qui doit contenir le mot clé ou le nom de clé défini et vérifiez qu'il est inclus dans votre fichier de ressources. Assurez-vous aussi que le mot clé ou le nom de clé est correctement orthographié. Si votre projet a été créé avec un en-tête précompilé et que vous le supprimez par la suite, assurez-vous que le fichier de ressources contient toujours les en-têtes nécessaires.

Pour vérifier les mots clés et les noms de clé définis dans votre fichier de ressources, dans Visual Studio, ouvrez la fenêtre **affichage des ressources** . dans la barre de menus, choisissez **Afficher**, **affichage des ressources**, puis ouvrez le menu contextuel du fichier. RC et choisissez **symboles des ressources** pour afficher la liste des symboles définis. Pour modifier les en-têtes inclus, ouvrez le menu contextuel du fichier. RC et choisissez **include des ressources**.

Si vous obtenez le message suivant :

```
undefined keyword or key name: MFT_STRING
```

ouvrez \MCL\MFC\Include\AfxRes.h et ajoutez cette directive include :

```
#include <winresrc.h>
```
