---
title: Fichiers de ressources (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 65500644b70841f372edcc6911edefc6c7b9f432
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152688"
---
# <a name="resource-files-c"></a>Fichiers de ressources (C++)

> [!NOTE]
> Ces informations s’appliquent aux applications de bureau Windows. Pour plus d’informations sur les ressources dans les applications de plateforme Windows universelle, consultez [définition des ressources d’application](/windows/uwp/app-resources/).
>
> Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).
>
> Comme les projets écrits dans les langages de programmation .NET managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de l’ **Explorateur de solutions**. Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Le terme « fichier de ressource » peut faire référence à différents types de fichiers, notamment :

- Le fichier de script de ressources (.rc) d’un programme

- Un fichier de modèle de ressource (.rct)

- Une ressource individuelle existant en tant que fichier autonome, telle qu’une bitmap, une icône ou un fichier curseur référencé à partir d’un fichier .rc

- Un fichier d’en-tête généré par l’environnement de développement, par exemple Resource.h, référencé à partir d’un fichier .rc

Ressources sont trouvent également dans [autres types de fichiers](../windows/editable-file-types-for-resources.md) tels que les fichiers .exe, .dll et .res. Vous pouvez travailler avec les ressources et à partir des fichiers de ressources au sein de votre projet et celles qui ne font pas partie de votre projet actuel. Vous pouvez également travailler avec des fichiers de ressources qui n’ont pas été créés dans l’environnement de développement de Visual Studio. Par exemple, vous pouvez :

- Travailler avec des fichiers de ressources imbriqués et inclus de manière conditionnelle

- Mettre à jour des ressources existantes ou les convertir au format Visual C++

- Importer ou exporter des ressources graphiques vers ou à partir de votre fichier de ressources actif

- Inclure des identificateurs partagés ou en lecture seule  (symboles) qui ne peuvent pas être modifiés par l’environnement de développement

- Inclure des ressources dans votre fichier exécutable (.exe) qui ne nécessitent une modification (ou qui ne doit pas être modifiée) lors de votre projet actuel, telles que des ressources partagées entre plusieurs projets.

- Inclure des types de ressources non pris en charge par l’environnement de développement

Vous pouvez ouvrir les types de fichiers suivants et modifier les ressources qu’ils contiennent :

|Nom de fichier|Description|
|---------------|-----------------|
|.rc|Fichiers de script de ressources.|
|.rct|Fichiers modèles de ressources.|
|.res|Fichiers de ressources.|
|.resx|Fichiers de ressources managées.|
|.exe|Fichiers exécutables.|
|.dll|Fichiers bibliothèques de liens dynamiques.|
|.bmp, .ico, .dib et .cur|Fichiers bitmap, icône, barre d'outils et curseur.|

L’environnement Visual Studio fonctionne avec et affecte les fichiers indiqués dans le tableau ci-dessous pendant votre session d’édition de ressource :

|Nom de fichier|Description|
|---------------|-----------------|
|Resource.h|Fichier d'en-tête généré par l'environnement de développement. Il contient les définitions de symbole. (Inclure ce fichier dans le contrôle de code source.)|
|Filename.aps|Version binaire du fichier de script de ressources actif. Ce fichier est utilisé pour le chargement rapide.<br /><br /> Les éditeurs de ressources ne lisent pas directement les fichiers .rc ou resource.h. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme le processus de compilation avec un élément normal, informations non symboliques (par exemple, les commentaires) sont ignorées pendant le processus de compilation. Chaque fois que le fichier .aps n'est plus synchronisé au fichier .rc, le fichier .rc est régénéré (par exemple, quand vous effectuez un enregistrement, l'éditeur de ressources remplace les fichiers .rc et resource.h). Les changements apportés aux ressources sont conservés dans le fichier .rc, mais les commentaires disparaissent une fois le fichier .rc remplacé. Pour plus d’informations sur la façon de conserver les commentaires, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md). (En règle générale, vous ne doit pas inclure le fichier .aps dans le contrôle de code source.)|
|.rc|Fichier de script de ressources qui contient le script des ressources de votre projet actif. Ce fichier est remplacé par le fichier .aps à chaque enregistrement. (Inclure ce fichier dans le contrôle de code source.)|

Cette section explique comment :

- [Créer des ressources](../windows/how-to-create-a-resource-script-file.md)

- [Gérer les ressources](../windows/how-to-copy-resources.md)

- [Inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md)

## <a name="manifest-resources"></a>Ressources de manifeste

Dans les projets de bureau C++, les ressources de manifeste sont des fichiers XML qui décrivent les dépendances qu’une application utilise. Par exemple, dans Visual Studio, le fichier manifeste généré par l'Assistant MFC définit la DLL de contrôle commun Windows que l'application doit utiliser, version 5.0 ou 6.0 :

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Pour une application Windows XP ou Windows Vista, la ressource de manifeste indique non seulement que l’application utiliser la version la plus récente des contrôles communs Windows, version 6.0, comme indiqué ci-dessus, mais il prend également en charge la [contrôle Syslink](/windows/desktop/Controls/syslink-overview).

Pour afficher la version et tapez les informations contenues dans une ressource de manifeste, vous pouvez ouvrir le fichier dans une visionneuse XML ou dans l’éditeur de texte Visual Studio. Si vous ouvrez une ressource de manifeste à partir de la fenêtre [Affichage des ressources](../windows/resource-view-window.md), la ressource s'ouvre au format binaire. Pour afficher le contenu d’une ressource de manifeste dans un format plus lisible, vous devez ouvrir la ressource à partir de **l’Explorateur de solutions**.

Pour ouvrir une ressource de manifeste, choisissez parmi les étapes suivantes :

- Pour l’éditeur de texte, avec votre projet ouvert dans **l’Explorateur de solutions**, développez le **fichiers de ressources** dossier et double-cliquez sur le fichier .manifest.

- Pour un autre éditeur, dans **l’Explorateur de solutions**, cliquez sur le fichier .manifest et choisissez **ouvrir avec...**  dans le menu contextuel. Dans le **ouvrir avec** boîte de dialogue, spécifiez l’éditeur que vous souhaitez utiliser, puis sélectionnez **Open**.

> [!NOTE]
> Vous ne pouvez avoir qu'une seule ressource de manifeste par module.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Menus et autres ressources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Contrôles](../mfc/controls-mfc.md)<br/>