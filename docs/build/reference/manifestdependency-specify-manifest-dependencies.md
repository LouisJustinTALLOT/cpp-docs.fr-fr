---
title: /MANIFESTDEPENDENCY (Spécifier les dépendances de manifeste)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: 676059b8d398fd108d8f8fc163c85a3da3c657b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321590"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Spécifier les dépendances de manifeste)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Notes

/MANIFESTDEPENDENCY vous permet de spécifier des attributs qui seront placés dans le \<dépendance > section du fichier manifeste.

Consultez [/MANIFEST (manifeste d’Assembly côte à côte de créer)](manifest-create-side-by-side-assembly-manifest.md) pour plus d’informations sur la création d’un fichier manifeste.

Pour plus d’informations sur la \<dépendance > section du fichier manifeste, consultez [les fichiers de Configuration de serveur de publication](/windows/desktop/SbsCs/publisher-configuration-files).

Les informations /MANIFESTDEPENDENCY peuvent être passées à l’éditeur de liens de deux manières :

- Directement sur la ligne de commande (ou dans un fichier réponse) avec /MANIFESTDEPENDENCY.

- Via le [commentaire](../../preprocessor/comment-c-cpp.md) pragma.

L’exemple suivant montre un commentaire /MANIFESTDEPENDENCY passé via ce pragma :

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

ce qui entraîne l’entrée suivante dans le fichier manifeste :

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Les mêmes commentaires /MANIFESTDEPENDENCY peuvent être passées à la ligne de commande comme suit :

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

L’éditeur de liens sera collecter des commentaires /MANIFESTDEPENDENCY, éliminer les entrées en double, puis ajoutez la chaîne XML qui en résulte dans le fichier manifeste.  Si l’éditeur de liens recherche des entrées en conflit, le fichier manifeste est endommagé et l’application échoue lancer (une entrée peut-être être ajoutée au journal des événements, indiquant la source de l’échec).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **le fichier manifeste** page de propriétés.

1. Modifier le **les dépendances de manifeste supplémentaires** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
