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
ms.openlocfilehash: 80833980b64e8fdd2a2f57b2dc40eb21c784b6f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232701"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Symbole de point d'entrée)

```
/ENTRY:function
```

## <a name="arguments"></a>Arguments

*function*<br/>
Fonction qui spécifie une adresse de départ définie par l’utilisateur pour un fichier. exe ou une DLL.

## <a name="remarks"></a>Notes

L’option/ENTRY spécifie une fonction de point d’entrée comme adresse de départ pour un fichier. exe ou une DLL.

La fonction doit être définie pour utiliser la **`__stdcall`** Convention d’appel. Les paramètres et la valeur de retour dépendent de si le programme est une application console, une application Windows ou une DLL. Il est recommandé de laisser l’éditeur de liens définir le point d’entrée de sorte que la bibliothèque Runtime C soit initialisée correctement et que les constructeurs C++ pour les objets statiques soient exécutés.

Par défaut, l’adresse de départ est un nom de fonction de la bibliothèque Runtime C. L’éditeur de liens le sélectionne conformément aux attributs du programme, comme indiqué dans le tableau suivant.

|Nom de la fonction|Par défaut pour|
|-------------------|-----------------|
|**mainCRTStartup** (ou **wmainCRTStartup**)|Une application qui utilise/SUBSYSTEM : CONSOLE ; appels `main` (ou `wmain` )|
|**WinMainCRTStartup** (ou **wWinMainCRTStartup**)|Une application qui utilise/SUBSYSTEM :**Windows**; appelle `WinMain` (ou `wWinMain` ), qui doit être défini pour utiliser**`__stdcall`**|
|**_DllMainCRTStartup**|UNE DLL ; appelle `DllMain` s’il existe, qui doit être défini pour utiliser**`__stdcall`**|

Si l’option [/dll](dll-build-a-dll.md) ou [/Subsystem](subsystem-specify-subsystem.md) n’est pas spécifiée, l’éditeur de liens sélectionne un sous-système et un point d’entrée selon que `main` ou `WinMain` est défini.

Les fonctions `main` , `WinMain` et `DllMain` sont les trois formes du point d’entrée défini par l’utilisateur.

Lors de la création d’une image managée, la fonction spécifiée pour/ENTRY doit avoir une signature (LPVOID *var1*, DWORD *var2*, LPVOID *var3*).

Pour plus d’informations sur la façon de définir votre propre `DllMain` point d’entrée, consultez [dll et Visual C++ comportement de la bibliothèque Runtime](../run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **avancé** .

1. Modifiez la propriété du **point d’entrée** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
