---
title: -ENTRÉE (symbole de Point d’entrée) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
dev_langs:
- C++
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74d7e6e05af98bb3d3175d352fb3d5de1b70b12b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375397"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Symbole de point d'entrée)
```  
/ENTRY:function  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *function*  
 Une fonction qui spécifie un démarrage définie par l’utilisateur une adresse pour un fichier .exe ou une DLL.  
  
## <a name="remarks"></a>Notes  
 L’option /ENTRY spécifie une fonction de point d’entrée comme adresse de départ pour un fichier .exe ou une DLL.  
  
 La fonction doit être définie pour utiliser le `__stdcall` convention d’appel. Les paramètres et la valeur de retour dépendant si le programme est une application console, une application windows ou une DLL. Il est recommandé de laisser l’éditeur de liens définir le point d’entrée afin que la bibliothèque Runtime C est initialisée correctement et que les constructeurs C++ d’objets statiques sont exécutés.  
  
 Par défaut, l’adresse de départ est un nom de fonction à partir de la bibliothèque Runtime C. L’éditeur de liens sélectionne selon les attributs du programme, comme indiqué dans le tableau suivant.  
  
|Nom de la fonction|Valeur par défaut pour|  
|-------------------|-----------------|  
|**mainCRTStartup** (ou **wmainCRTStartup**)|Une application qui utilise/SUBSYSTEM : console ; appels `main` (ou `wmain`)|  
|**WinMainCRTStartup** (ou **wWinMainCRTStartup**)|Une application qui utilise/SUBSYSTEM :**WINDOWS**; appels `WinMain` (ou `wWinMain`), qui doit être défini à utiliser `__stdcall`|  
|**_DllMainCRTStartup**|UNE DLL ; appels `DllMain` si elle existe, qui doit être défini à utiliser `__stdcall`|  
  
 Si le [/DLL](../../build/reference/dll-build-a-dll.md) ou [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) option n’est pas spécifiée, l’éditeur de liens sélectionne un sous-système de point d’entrée selon que `main` ou `WinMain` est défini.  
  
 Les fonctions `main`, `WinMain`, et `DllMain` sont les trois formes du point d’entrée défini par l’utilisateur.  
  
 Lorsque vous créez une image managée, la fonction spécifiée à /ENTRY doit avoir une signature de (LPVOID *var1*, DWORD *var2*, LPVOID *var3*).  
  
 Pour plus d’informations sur la façon de définir vos propres `DllMain` point d’entrée, consultez [DLL et Visual C++ comportement de la bibliothèque d’exécution](../../build/run-time-library-behavior.md) .  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **avancé** page de propriétés.  
  
4.  Modifier la **Point d’entrée** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)