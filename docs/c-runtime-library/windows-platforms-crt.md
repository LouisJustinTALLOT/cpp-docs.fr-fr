---
title: Plateformes Windows (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility [C++], C run-time libraries
- compatibility [C++], C run-time libraries
- MBCS [C++], Win32 platforms
- operating systems [C++]
- Unicode [C++], Win32 platforms
ms.assetid: 0aacaf45-6dc4-4908-bd52-57abac7b39f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d53e8020bbb7649d78232025ef9c63c1dc868fee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409005"
---
# <a name="windows-platforms-crt"></a>Plateformes Windows (CRT)

Les bibliothèques Runtime C pour Visual Studio prennent en charge les versions actuelles de Windows et Windows Server, [!INCLUDE[win8](../build/reference/includes/win8_md.md)], [!INCLUDE[winserver8](../build/reference/includes/winserver8_md.md)], [!INCLUDE[win7](../build/includes/win7_md.md)], [!INCLUDE[winsvr08](../build/reference/includes/winsvr08_md.md)] et Windows Vista. Elles prennent éventuellement en charge [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3) pour x86, [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) x64, et [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2) x86 et x64. Tous ces systèmes d’exploitation prennent en charge l’API de bureau Windows (Win32) et fournissent la prise en charge d’Unicode. En outre, toute application Win32 peut utiliser un jeu de caractères multioctets (MBCS).

> [!NOTE]
> L’installation par défaut de la charge de travail **Développement Desktop en C++** dans Visual Studio 2017 n’inclut pas la prise en charge du développement de [!INCLUDE[winxp](../build/includes/winxp_md.md)] et [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Vous devez installer le composant facultatif **Prise en charge de Windows XP pour C++** pour activer un ensemble d’outils de plateforme Windows XP.

## <a name="see-also"></a>Voir aussi

[Compatibilité](../c-runtime-library/compatibility.md)  
