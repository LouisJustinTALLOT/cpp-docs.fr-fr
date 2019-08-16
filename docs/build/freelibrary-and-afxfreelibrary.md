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
ms.openlocfilehash: 9c657bb0d583270f81658afa53f36b1be6a4fd4a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493262"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary et AfxFreeLibrary

Les processus qui sont explicitement liés à une DLL appellent la fonction [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary) lorsque le module dll n’est plus nécessaire. Cette fonction décrémente le nombre de références du module et, si le nombre de références est égal à zéro, la démappe de l’espace d’adressage du processus.

Dans une application MFC, utilisez [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) au lieu `FreeLibrary` de pour décharger une DLL d’extension MFC. L’interface (prototype de fonction) `AfxFreeLibrary` pour est identique à `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [LoadLibrary et AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
