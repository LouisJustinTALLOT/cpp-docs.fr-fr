---
title: Automation dans une DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 3cc5ca456842707a2c3de7b2fd74abc73d9a5307
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422284"
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

[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)
