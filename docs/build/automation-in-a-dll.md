---
title: Automation dans une DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220918"
---
# <a name="automation-in-a-dll"></a>Automation dans une DLL

Lorsque vous choisissez l’option Automation dans l’Assistant DLL MFC, l’Assistant vous offre les éléments suivants :

- Un langage de description d’objet starter (. Fichier ODL)

- Une directive include dans le fichier STDAFX.h pour Afxole.h

- Une implémentation de la `DllGetClassObject` (fonction), qui appelle le **AfxDllGetClassObject** (fonction)

- Une implémentation de la `DllCanUnloadNow` (fonction), qui appelle le **AfxDllCanUnloadNow** (fonction)

- Une implémentation de la `DllRegisterServer` (fonction), qui appelle le [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) (fonction)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Serveurs Automation](../mfc/automation-servers.md)

## <a name="see-also"></a>Voir aussi

[Créer des DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
