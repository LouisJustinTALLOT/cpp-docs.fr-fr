---
title: Prise en charge MFC dans les projets ATL
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 0aece6805f1de987b0164f405e50b99fd706fef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275423"
---
# <a name="mfc-support-in-atl-projects"></a>Prise en charge MFC dans les projets ATL

Si vous sélectionnez **prise en charge MFC** dans l’Assistant Projet ATL, votre projet déclare l’application en tant qu’objet application MFC (classe). Le projet initialise la bibliothèque MFC et instancie une classe (classe *ProjName*) qui est dérivée de [CWinApp](../../mfc/reference/cwinapp-class.md).

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

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
