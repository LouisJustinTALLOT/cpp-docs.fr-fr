---
title: /ENTRY (Symbole de point d'entrée)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 0f3604ef75ce10928463c088e423615886555eda
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807856"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Symbole de point d'entrée)

```
/ENTRY:function
```

## <a name="arguments"></a>Arguments

*function*<br/>
Une fonction qui spécifie de départ définie par l’utilisateur d’adresses pour un fichier .exe ou une DLL.

## <a name="remarks"></a>Notes

L’option /ENTRY spécifie une fonction de point d’entrée comme adresse de départ pour un fichier .exe ou une DLL.

La fonction doit être définie pour utiliser le `__stdcall` convention d’appel. Les paramètres et la valeur de retour varient selon si le programme est une application console, une application windows ou une DLL. Il est recommandé de laisser l’éditeur de liens définir le point d’entrée afin que la bibliothèque Runtime C est initialisée correctement et que les constructeurs C++ d’objets statiques sont exécutés.

Par défaut, l’adresse de départ est un nom de fonction à partir de la bibliothèque Runtime C. L’éditeur de liens sélectionne selon les attributs du programme, comme indiqué dans le tableau suivant.

|Nom de la fonction|Valeur par défaut pour|
|-------------------|-----------------|
|**mainCRTStartup** (ou **wmainCRTStartup**)|Une application qui utilise/SUBSYSTEM : console ; appels `main` (ou `wmain`)|
|**WinMainCRTStartup** (ou **wWinMainCRTStartup**)|Une application qui utilise /SUBSYSTEM :**WINDOWS**; appels `WinMain` (ou `wWinMain`), qui doit être défini à utiliser `__stdcall`|
|**_DllMainCRTStartup**|UNE DLL ; appels `DllMain` si elle existe, qui doit être défini à utiliser `__stdcall`|

Si le [/DLL](dll-build-a-dll.md) ou [/SUBSYSTEM](subsystem-specify-subsystem.md) option n’est pas spécifiée, l’éditeur de liens sélectionne un sous-système de point d’entrée selon que `main` ou `WinMain` est défini.

Les fonctions `main`, `WinMain`, et `DllMain` sont les trois formes du point d’entrée défini par l’utilisateur.

Lorsque vous créez une image managée, la fonction spécifiée à/ENTRY doit avoir une signature de (LPVOID *var1*, DWORD *var2*, LPVOID *var3*).

Pour plus d’informations sur la façon de définir les vôtres `DllMain` point d’entrée, consultez [DLL et Visual C++ comportement de la bibliothèque du run-time](../run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **Point d’entrée** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
