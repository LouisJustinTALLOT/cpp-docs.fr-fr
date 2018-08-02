---
title: Ajouter des caractères spéciaux ou de mise en forme une chaîne | Microsoft Docs
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
ms.openlocfilehash: 35592793b0fe606d3b88bef900d528d2c1231406
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463838"
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>Ajout de caractères de mise en forme ou de caractères spéciaux à une chaîne
### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Pour ajouter des caractères spéciaux ou de mise en forme à une chaîne  
  
1.  Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Sélectionnez la chaîne que vous souhaitez modifier.  
  
3.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ajouter du texte dans des séquences d’échappement standard figurant ci-dessous le **légende** zone, puis appuyez sur **entrée**.  
  
    |Pour résoudre ce|Ce type|  
    |-----------------|---------------|  
    |Nouvelle ligne|\n|  
    |Retour chariot|\r|  
    |Onglet|\t|  
    |Barre oblique inverse (\\)|\\\|  
    |Caractère ASCII|\ddd (notation octale)|  
    |alerte (clochette)|\a|  
  
> [!NOTE]
>  L’éditeur de chaînes ne prend pas en charge l’ensemble complet d’échappement des caractères d’ASCII. Vous ne pouvez utiliser que ceux répertoriés ci-dessus.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) et [Procédure pas à pas : utilisation des ressources pour la localisation avec ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de chaînes](../windows/string-editor.md)   

