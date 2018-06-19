---
title: Prise en charge MFC dans les projets ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.addmfc
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d42afec863695b1cab05c2d3cf2f65f3d64a1507
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360639"
---
# <a name="mfc-support-in-atl-projects"></a>Prise en charge MFC dans les projets ATL
Si vous sélectionnez **prise en charge MFC** dans l’Assistant Projet ATL, votre projet déclare l’application en tant qu’objet application MFC (classe). Le projet initialise la bibliothèque MFC et instancie une classe (classe *NomProj*) qui est dérivée de [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Cette option est disponible pour les projets DLL ATL sans attributs.  
  
```  
class CProjNameApp : public CWinApp  
{  
public:  
 
// Overrides  
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP() 
};  
 
BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)  
END_MESSAGE_MAP()  
 
CProjNameApp theApp;  
 
BOOL CProjNameApp::InitInstance()  
{  
    return CWinApp::InitInstance();

}  
 
int CProjNameApp::ExitInstance()  
{  
    return CWinApp::ExitInstance();

}  
```  
  
 Vous pouvez afficher la classe d’objet application et ses `InitInstance` et `ExitInstance` fonctions dans l’affichage de classes.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)   
 [Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)   
 [Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)

