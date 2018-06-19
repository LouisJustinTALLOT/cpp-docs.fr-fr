---
title: Ajout de caractères spéciaux ou de mise en forme en une chaîne | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 429ba8d836579bd3bc1d1dd8844494bf9cd17a7a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864595"
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>Ajout de caractères de mise en forme ou de caractères spéciaux à une chaîne
### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Pour ajouter des caractères spéciaux ou de mise en forme à une chaîne  
  
1.  Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Sélectionnez la chaîne que vous souhaitez modifier.  
  
3.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ajouter des séquences d’échappement standard répertoriées ci-dessous à du texte dans le **légende** zone, puis appuyez sur **entrée**.  
  
    |Pour obtenir ce|Tapez ce qui suit|  
    |-----------------|---------------|  
    |Nouvelle ligne|\n|  
    |Retour chariot|\r|  
    |Onglet|\t|  
    |Barre oblique inverse (\\)|\\\|  
    |Caractère ASCII|\ddd (notation octale)|  
    |Alerte (clochette)|\a|  
  
> [!NOTE]
>  L’éditeur de chaînes ne prend pas en charge l’ensemble complet de caractères ASCII d’échappement. Vous ne pouvez utiliser que ceux répertoriés ci-dessus.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, et ceci manuellement, consultez [Procédure pas à pas : localisation des applications Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) et [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de chaînes](../windows/string-editor.md)   

