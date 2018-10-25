---
title: Y compris partagés (lecture seule) ou calculés symboles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.shared.calculated
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a2bb3a95f2b9e5506ee761906a7df213f97b927
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061792"
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>Ajout de symboles partagés (lecture seule) ou calculés

La première fois que l'environnement de développement lit un fichier de ressources créé par une autre application, il marque tous les fichiers d'en-tête inclus en lecture seule. Par la suite, vous pouvez utiliser la [boîte de dialogue Include des ressources](../windows/resource-includes-dialog-box.md) pour ajouter des fichiers d’en-tête de symbole en lecture seule.

Si vous envisagez de partager des fichiers de symboles entre plusieurs projets, vous pouvez utiliser les définitions de symbole en lecture seule.

Vous pouvez également utiliser des fichiers de symboles inclus quand vous disposez de ressources avec des définitions de symbole qui utilisent des expressions au lieu d'entiers simples pour définir la valeur du symbole. Exemple :

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

L'environnement interprète correctement ces symboles calculés tant que les conditions suivantes sont respectées :

- Les symboles calculés sont placés dans un fichier de symboles en lecture seule.

- Votre fichier de ressources contient des ressources auxquelles ces symboles calculés sont déjà assignés.

- Une expression numérique est attendue.

> [!NOTE]
> Si une chaîne ou une expression numérique est attendue, l'expression n'est pas évaluée.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Pour inclure des symboles partagés (en lecture seule) dans votre fichier de ressources

1. Dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur votre fichier .rc et choisissez [Include des ressources](../windows/resource-includes-dialog-box.md) dans le menu contextuel.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Dans le **directives de symboles en lecture seule** zone, utilisez la `#include` directive de compilateur pour spécifier le fichier dans lequel les symboles en lecture seule peuvent être conservées.

   N’appelez pas le fichier `Resource.h`, puisque c’est le nom de fichier utilisé normalement par le fichier d’en-tête de symbole principal.

   > [!NOTE]
   > **Important** ce que vous tapez dans la zone directives de symbole en lecture seule est inclus dans le fichier de ressources exactement comme vous le tapez. Vérifiez que ce que vous tapez ne contient aucune erreur d'orthographe ou de syntaxe.

   Utilisez le **directives de symboles en lecture seule** case pour inclure les fichiers contenant uniquement les définitions de symbole. N'incluez pas de définitions de ressource. Sinon, des définitions de ressource en double seront créées durant l'enregistrement du fichier.

3. Placez les symboles dans le fichier spécifié.

   Les symboles contenus dans les fichiers inclus de cette façon sont évalués chaque fois que vous ouvrez votre fichier de ressources. Toutefois, ils ne sont pas remplacés sur le disque quand vous enregistrez votre fichier.

4. Cliquez sur **OK**.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md)<br/>
[Restrictions relatives à la valeur d’un symbole](../windows/symbol-value-restrictions.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)