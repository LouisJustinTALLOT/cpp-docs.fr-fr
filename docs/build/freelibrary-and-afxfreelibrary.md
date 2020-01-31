---
title: FreeLibrary et AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: 0b530aca2ab036de186ff3fdb11be23f41e12d05
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821549"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary et AfxFreeLibrary

Les processus qui sont explicitement liés à une DLL appellent la fonction [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary) lorsque le module dll n’est plus nécessaire. Cette fonction décrémente le décompte de références du module. Et, si le nombre de références est égal à zéro, il est non mappé à partir de l’espace d’adressage du processus.

Dans une application MFC, utilisez [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) au lieu de `FreeLibrary` pour décharger une DLL d’extension MFC. L’interface (prototype de fonction) de `AfxFreeLibrary` est identique à `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [LoadLibrary et AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Voir aussi

[Créer des CC++ /dll dans Visual Studio](dlls-in-visual-cpp.md)\
\ [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
