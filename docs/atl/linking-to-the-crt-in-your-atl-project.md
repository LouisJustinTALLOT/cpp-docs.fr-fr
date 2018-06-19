---
title: Liaison vers le CRT dans votre projet ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- DllMainCRTStartup
- wWinMainCRTStartup
- WinMainCRTStartup
dev_langs:
- C++
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec0d93f8770ebbd893491c0e8b8eed239396e00a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356381"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Liaison vers le CRT dans votre projet ATL
Le [C Run-Time Libraries](../c-runtime-library/crt-library-features.md) (CRT) fournissent de nombreuses fonctions qui facilitent le programmation pendant le développement ATL. Tous les projets ATL lier à la bibliothèque CRT. Vous pouvez voir les avantages et inconvénients de la liaison de méthode dans [avantages et limitations de la méthode utilisée pour le lien vers la bibliothèque CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Effets de la liaison vers le CRT sur l’Image de votre programme  
 Si vous liez statiquement à la bibliothèque CRT, le code à partir de la bibliothèque CRT est placé dans votre image exécutable et vous n’avez pas besoin de disposer de la DLL CRT présents sur un système pour exécuter votre image. Si vous liez dynamiquement à la bibliothèque CRT, les références au code dans la DLL CRT sont placés dans votre image, mais pas le code lui-même. Dans l’ordre de votre image pour s’exécuter sur un système donné, la DLL CRT doit être présente sur ce système. Même lorsque vous liez dynamiquement à la bibliothèque CRT, vous découvrirez peut-être que du code peut être lié statiquement (par exemple, **DllMainCRTStartup**).  
  
 Lorsque vous liez votre image, implicitement ou explicitement spécifier un point d’entrée que le système d’exploitation appellera après le chargement de l’image. Pour une DLL, le point d’entrée par défaut est **DllMainCRTStartup**. Pour un EXE, il est **WinMainCRTStartup**. Vous pouvez remplacer la valeur par défaut avec l’option de l’éditeur de liens /ENTRY. La bibliothèque CRT fournit une implémentation pour **DllMainCRTStartup**, **WinMainCRTStartup**, et **wWinMainCRTStartup** (le point d’entrée Unicode pour un EXE). Ces points d’entrée fournis par le CRT appellent des constructeurs sur des objets globaux et initialiser les autres structures de données qui sont utilisées par certaines fonctions CRT. Ce code de démarrage ajoute environ 25 Ko à votre image si elle est liée de manière statique. S’il est lié dynamiquement, la plupart du code est dans la DLL, la taille de votre image reste petite.  
  
 Pour plus d’informations, consultez la rubrique de l’éditeur de liens [/ENTRY (symbole de Point d’entrée)](../build/reference/entry-entry-point-symbol.md).  
  
## <a name="optimization-options"></a>Options d’optimisation  
 À l’aide de l’option de l’éditeur de liens/OPT : NOWIN98 permet de réduire un contrôle ATL par défaut de 10 K, aux dépens des produits augmentée du temps sur les systèmes Windows 98 de chargement. Pour plus d’informations sur la liaison des options, consultez [/OPT (optimisations)](../build/reference/opt-optimizations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec ATL et le Code d’exécution C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [DLL et comportement de la bibliothèque runtime Visual C++](../build/run-time-library-behavior.md)

