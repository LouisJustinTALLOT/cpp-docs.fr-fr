---
title: Rendre un objet ATL comme Noncreatable | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05707c6771d641d383825a07d0b26a90fdf46cb1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358259"
---
# <a name="making-an-atl-object-noncreatable"></a>Rendre un objet ATL comme Noncreatable
Vous pouvez modifier les attributs d’un objet COM fondés sur ATL afin qu’un client ne peut pas créer directement l’objet. Dans ce cas, l’objet serait être retournée via un appel de méthode sur un autre objet au lieu créé directement.  
  
### <a name="to-make-an-object-noncreatable"></a>Pour rendre un objet comme noncreatable  
  
1.  Supprimer le [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour l’objet. Si vous souhaitez que l’objet comme noncreatable mais le contrôle à inscrire, remplacez OBJECT_ENTRY_AUTO avec [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).  
  
2.  Ajouter le [noncreatable](../../windows/noncreatable.md) d’attribut à la coclasse dans le fichier .idl. Par exemple :  
  
 ```  
 [  
    uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
 {  
 [default] interface IMyInterface;  
 }  
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)   
 [Types de projet Visual C++](../../ide/visual-cpp-project-types.md)   
 [Création de projets du Bureau à l’aide des Assistants Application](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programmation avec ATL et le Code d’exécution C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Notions de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)

