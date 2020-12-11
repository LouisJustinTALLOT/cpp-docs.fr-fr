---
description: 'En savoir plus sur : prise en charge MFC dans les projets ATL'
title: Prise en charge MFC dans les projets ATL
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 8614bfdd5320e0ecdf34cc96251fa8a20f2dede9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157917"
---
# <a name="mfc-support-in-atl-projects"></a>Prise en charge MFC dans les projets ATL

Si vous sélectionnez **prendre en charge MFC** dans l’Assistant Projet ATL, votre projet déclare l’application en tant qu’objet application MFC (classe). Le projet initialise la bibliothèque MFC et instancie une classe (classe *ProjName*) dérivée de [CWinApp](../../mfc/reference/cwinapp-class.md).

Cette option est disponible uniquement pour les projets DLL ATL sans attributs.

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

Vous pouvez afficher la classe d’objets d’application et ses `InitInstance` `ExitInstance` fonctions et dans affichage de classes.

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
