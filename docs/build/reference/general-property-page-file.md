---
title: Général, page de propriétés (Fichier)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 41366e2eae479c3d00f79cc47da9100b22129d50
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218185"
---
# <a name="general-property-page-file"></a>Général, page de propriétés (Fichier)

Cette rubrique s’applique aux projets Windows. Pour les projets autres que Windows, [consultez C++ référence de la page de propriétés Linux](../../linux/prop-pages-linux.md).

Lorsque vous cliquez avec le bouton droit sur un nœud de fichier **Explorateur de solutions**, la page de propriétés **général** sous le nœud **Propriétés de configuration** s’ouvre. Il contient les propriétés suivantes:

- **Exclu de la Build**

   Spécifie si le fichier doit se trouver dans la génération de la configuration actuelle.

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Contenu** (S’applique uniquement aux applications UWP.) Spécifie si le fichier contient du contenu à inclure dans le package d’application.

- **Type d’élément**

   Le **type d’élément** spécifie l’outil qui sera utilisé pour traiter le fichier pendant le processus de génération. Les [fichiers dont l’extension est connue de Visual Studio](/visualstudio/extensibility/visual-cpp-project-extensibility?view=vs-2019#project-items) ont une valeur par défaut dans cette propriété. Vous pouvez spécifier un outil personnalisé ici si vous disposez d’un type de fichier personnalisé ou si vous souhaitez remplacer l’outil par défaut pour un type de fichier connu. Pour plus d’informations, consultez [Spécification des outils de génération personnalisée](../specifying-custom-build-tools.md). Vous pouvez également utiliser cette page de propriétés pour spécifier qu’un fichier ne fait pas partie du processus de génération.

   L’illustration suivante montre la page de propriétés d’un fichier *. cpp* . Le **type d’élément** par défaut pour ce genre de fichier est le **compilateur C/C++**  (*CL. exe*) et la page de propriétés expose différents paramètres de compilateur qui peuvent être appliqués à ce fichier uniquement.

   ![Page de propriétés général d’un élément de projet](media/file-general-item-type.png "Choix du type d’élément")

    Le tableau suivant répertorie les types d’éléments par défaut:

    |Extension de fichier|Type d'élément|Outil par défaut|
    |-|-|-|
    |. AppX|Définition de l’application XAML|[Package App Pack](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. HLSL,. CSO|Compilateur HLSL|[fxc. exe](/windows/win32/direct3dtools/fxc)|
    |.h|C/C++ en-tête|[Préprocesseur C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |N/A|Ne participe pas à la Build|N/A|
    |. xml,. XSLT,. Xsl|xml|[Éditeur XML](/visualstudio/xml-tools/xml-editor)|
    |. resw,. resjson|Ressource PRI (applications UWP)|[MakePri. exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||Support (UWP)|[Package App Pack](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. xsd|Outil XML Data Generator Tool|[Outil XML Schema Definition (XSD. exe)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) (Nécessite une charge de travail .NET. Non inclus dans MSVC.)|
    ||Outil Manifeste|[Mt. exe](/windows/win32/sbscs/mt-exe)|
    |.rc|Ressource|[Compilateur de ressources Windows (RC. exe)](/windows/win32/menurc/resource-compiler)|
    |. appxmanifest|Manifeste du package d’application|[Package App Pack](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Object|[C/C++ éditeur de liens (Link. exe)](cl-invokes-the-linker.md)|
    |. ttf|Police|N/A|
    |.txt|Text|N/A|
    |N/A|Outil de génération personnalisée|Défini par l’utilisateur|
    |N/A|Copier le fichier|N/A|
    |. appxlayout|Disposition de package d’application|[Package App Pack](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|Ressource gérée par le compilateur|[Resgen.exe (Resource File Generator)](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |. natvis|C++Fichier de visualisation du débogueur|[Framework Natvis](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |. jpg,. bmp,. ico, etc.|Image|Compilateur de ressources basé sur le type d’application.|
    |.cpp|C/C++ compilateur|CL. exe|

   Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Pour plus d’informations sur la façon d’accéder à la page de propriétés **général** sous le nœud **Propriétés de configuration** , consultez [ C++ définir les propriétés de compilation et de génération dans Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Voir aussi

[C++Référence de la page de propriétés du projet](property-pages-visual-cpp.md)