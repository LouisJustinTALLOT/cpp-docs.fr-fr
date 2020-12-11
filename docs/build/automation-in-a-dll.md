---
description: 'En savoir plus sur : Automation dans une DLL'
title: Automation dans une DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: e0d6d0beec71f3994f6e726c6946b2069d1b081b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163234"
---
# <a name="automation-in-a-dll"></a>Automation dans une DLL

Lorsque vous choisissez l’option Automation dans l’Assistant DLL MFC, l’Assistant vous fournit les éléments suivants :

- Un langage de description d’objet Starter (. Fichier ODL)

- Une directive include dans le fichier STDAFX. h pour AFXOLE. h

- Une implémentation de la `DllGetClassObject` fonction, qui appelle la fonction **AfxDllGetClassObject**

- Une implémentation de la `DllCanUnloadNow` fonction, qui appelle la fonction **AfxDllCanUnloadNow**

- Une implémentation de la `DllRegisterServer` fonction, qui appelle la fonction [COleObjectFactory :: UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Serveurs Automation](../mfc/automation-servers.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
