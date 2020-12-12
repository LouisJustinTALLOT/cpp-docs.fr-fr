---
description: En savoir plus sur:/DLL (générer une DLL)
title: /DLL (Générer une DLL)
ms.date: 11/04/2016
f1_keywords:
- /dll
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
ms.openlocfilehash: 42535fb15762e5c0f1691d5c28029c7368005f87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201402"
---
# <a name="dll-build-a-dll"></a>/DLL (Générer une DLL)

```
/DLL
```

## <a name="remarks"></a>Notes

L’option/DLL génère une DLL comme fichier de sortie principal. Une DLL contient généralement des exportations qui peuvent être utilisées par un autre programme. Il existe trois méthodes pour spécifier des exportations, répertoriées dans l’ordre d’utilisation recommandé :

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source

1. Une instruction [exports](exports.md) dans un fichier. def

1. Une spécification [/Export](export-exports-a-function.md) dans une commande Link

Un programme peut utiliser plusieurs méthodes.

Une autre façon de créer une DLL consiste à utiliser l’instruction de définition de module de **bibliothèque** . Les options/BASE et/DLL ensemble sont équivalentes à l’instruction **Library** .

Ne spécifiez pas cette option dans l’environnement de développement. Cette option est destinée à être utilisée uniquement sur la ligne de commande. Cette option est définie lorsque vous créez un projet DLL avec un Assistant Application.

Notez que si vous créez votre bibliothèque d’importation à une étape préliminaire, avant de créer votre fichier. dll, vous devez passer le même ensemble de fichiers objets lors de la génération du fichier. dll, comme vous l’avez passé lors de la génération de la bibliothèque d’importation.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Propriétés de configuration** .

1. Cliquez sur la page de propriétés **général** .

1. Modifiez la propriété **type de configuration** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
