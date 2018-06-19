---
title: Y compris partagés (lecture seule) ou calculés symboles | Documents Microsoft
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
- symbols, read-only
- symbols, shared
- symbols, calculated
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
ms.openlocfilehash: c56e8af65d27bda8ef04655f40bdd2e335067d3c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879225"
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>Ajout de symboles partagés (lecture seule) ou calculés
La première fois que l'environnement de développement lit un fichier de ressources créé par une autre application, il marque tous les fichiers d'en-tête inclus en lecture seule. Ensuite, vous pouvez utiliser la [boîte de dialogue Include des ressources](../windows/resource-includes-dialog-box.md) pour ajouter des fichiers d’en-tête de symbole en lecture seule.  
  
 Si vous envisagez de partager des fichiers de symboles entre plusieurs projets, vous pouvez utiliser les définitions de symbole en lecture seule.  
  
 Vous pouvez également utiliser des fichiers de symboles inclus quand vous disposez de ressources avec des définitions de symbole qui utilisent des expressions au lieu d'entiers simples pour définir la valeur du symbole. Par exemple :  
  
```  
#define   IDC_CONTROL1 2100  
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```  
  
 L'environnement interprète correctement ces symboles calculés tant que les conditions suivantes sont respectées :  
  
-   Les symboles calculés sont placés dans un fichier de symboles en lecture seule.  
  
-   Votre fichier de ressources contient des ressources auxquelles ces symboles calculés sont déjà assignés.  
  
-   Une expression numérique est attendue.  
  
> [!NOTE]
>  Si une chaîne ou une expression numérique est attendue, l'expression n'est pas évaluée.  
  
### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Pour inclure des symboles partagés (en lecture seule) dans votre fichier de ressources  
  
1.  Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc et choisissez [Include des ressources](../windows/resource-includes-dialog-box.md) dans le menu contextuel.  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans le **directives de symboles en lecture seule** , utilisez le **#include** directive de compilateur pour spécifier le fichier dans lequel les symboles en lecture seule sont conservés.  
  
     N'appelez pas le fichier Resource.h, car il s'agit du nom de fichier utilisé normalement par le fichier d'en-tête de symbole principal.  
  
    > [!NOTE]
    >  **Important** ce que vous tapez dans la zone directives de symbole en lecture seule est inclus dans le fichier de ressources exactement comme vous le tapez. Vérifiez que ce que vous tapez ne contient aucune erreur d'orthographe ou de syntaxe.  
  
     Utilisez le **directives de symboles en lecture seule** à cocher pour inclure les fichiers contenant uniquement les définitions de symbole. N'incluez pas de définitions de ressource. Sinon, des définitions de ressource en double seront créées durant l'enregistrement du fichier.  
  
3.  Placez les symboles dans le fichier spécifié.  
  
     Les symboles contenus dans les fichiers inclus de cette façon sont évalués chaque fois que vous ouvrez votre fichier de ressources. Toutefois, ils ne sont pas remplacés sur le disque quand vous enregistrez votre fichier.  
  
4.  Cliquez sur **OK**.  
  

  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md)   
 [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md)   
 [ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)   
 [Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)