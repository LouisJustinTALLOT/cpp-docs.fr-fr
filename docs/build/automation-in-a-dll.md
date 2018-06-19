---
title: Automation dans une DLL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41c5f31a72cf734296ecb281e0785d415c8043a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360652"
---
# <a name="automation-in-a-dll"></a>Automation dans une DLL
Lorsque vous choisissez l’option Automation dans l’Assistant DLL MFC, l’Assistant vous fournit les éléments suivants :  
  
-   Un ichier (. Fichier ODL)  
  
-   Une directive include dans le fichier STDAFX.h pour Afxole.h  
  
-   Une implémentation de la `DllGetClassObject` (fonction), qui appelle la **AfxDllGetClassObject** (fonction)  
  
-   Une implémentation de la `DllCanUnloadNow` (fonction), qui appelle la **AfxDllCanUnloadNow** (fonction)  
  
-   Une implémentation de la `DllRegisterServer` (fonction), qui appelle la [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) (fonction)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Serveurs Automation](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)