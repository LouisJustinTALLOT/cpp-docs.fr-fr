---
title: Fichiers de ressources (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 45db6d0139cfa3aa8a2eaa8fe6d18158cb6646ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387914"
---
# <a name="resource-files-c"></a>Fichiers de ressources (C++)

> [!NOTE]
> Comme les projets écrits dans les langages de programmation .NET managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de l’ **Explorateur de solutions**. Utilisez le [Éditeur d’images](../windows/image-editor-for-icons.md) et [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans les projets managés.
>
> Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Le terme *fichier de ressources* peuvent faire référence à un nombre de types de fichiers, par exemple :

- Le fichier de script de ressources (.rc) d’un programme

- Un fichier de modèle de ressource (.rct)

- Une ressource individuelle existant en tant que fichier autonome. Ce type inclut un fichier bitmap, icône ou curseur référencé à partir d’un fichier .rc.

- Un fichier d’en-tête généré par l’environnement de développement. Ce type inclut `Resource.h`, référencé à partir d’un fichier .rc.

Trouver des ressources dans d’autres types de fichier tels que les fichiers .exe, .dll et .res sont appelés *ressources*.

Vous pouvez travailler avec *fichiers de ressources* et *ressources* à partir de votre projet. Vous pouvez également travailler avec celles qui ne font pas partie du projet actuel ou ont été créés en dehors de l’environnement de développement de Visual Studio. Par exemple, vous pouvez :

- Travailler avec des fichiers de ressources imbriqués et inclus de manière conditionnelle

- Mettre à jour des ressources existantes ou les convertir en Visual C++.

- Importer ou exporter des ressources graphiques vers ou à partir de votre fichier de ressources actif

- Inclure des identificateurs partagés ou en lecture seule  (symboles) qui ne peuvent pas être modifiés par l’environnement de développement

- Inclure des ressources dans votre fichier exécutable (.exe) qui évite la modification (ou ne doit pas être modifié), telles que des ressources partagées entre plusieurs projets.

- Inclure des types de ressources non pris en charge par l’environnement de développement

Pour plus d’informations sur les ressources, consultez Comment [créer les ressources](../windows/how-to-create-a-resource-script-file.md), [gérer les ressources](../windows/how-to-copy-resources.md), et [comprenant des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Ressources modifiables

Les types de fichiers suivants peuvent être ouverts pour modifier les ressources qu’ils contiennent :

| Nom de fichier | Description |
|---|---|
| .rc | Fichiers de script de ressources |
| .rct | Fichiers de modèle de ressources |
| .res | Fichiers de ressources |
| .resx | Fichiers de ressources managés |
| .exe | Fichiers exécutables |
| .dll | Fichiers de bibliothèque de liens dynamiques |
| .bmp, .ico, .dib, .cur | Fichiers bitmap, icône, barre d’outils et curseur |

Lorsque vous modifiez des ressources, l’environnement Visual Studio fonctionne avec et affecte les fichiers suivants :

| Nom de fichier | Description |
|---|---|
| Resource.h | Fichier d’en-tête généré par l’environnement de développement qui contient les définitions de symbole.<br/><br/>Inclure ce fichier dans le contrôle de code source. |
| Filename.aps | Version binaire du fichier de script de ressources actuel utilisé pour le chargement rapide.<br /><br /> Éditeurs de ressources ne lisent pas directement les fichiers .rc ou resource.h. Le compilateur de ressources les compile en fichiers .aps qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques.<br/><br/>Comme le processus de compilation avec un élément normal, les informations non symboliques, tels que l’ajout de commentaires, sont ignorées pendant le processus de compilation.<br/><br/>Chaque fois que le fichier .aps n’est plus synchronisé avec le fichier .rc, le fichier .rc est régénéré. Par exemple, lorsque vous **enregistrer**, l’éditeur de ressources remplace le fichier .rc et resource.h. Les modifications apportées aux ressources continuent dans le fichier .rc, mais les commentaires seront perdus une fois que le fichier .rc est remplacé. Pour plus d’informations sur la façon de conserver les commentaires, consultez [comprenant des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>En règle générale, vous ne doit pas inclure le fichier .aps dans le contrôle de code source. |
| .rc | Fichier de script de ressources qui contient le script des ressources de votre projet actif. Ce fichier est remplacé par le fichier .aps à chaque enregistrement.<br/><br/>Inclure ce fichier dans le contrôle de code source. |

## <a name="manifest-resources"></a>Ressources de manifeste

Dans les projets de bureau C++, les ressources de manifeste sont des fichiers XML qui décrivent les dépendances de qu'une application utilise. Par exemple, dans Visual Studio cette MFC générées par l’Assistant fichier de manifeste définit quelle version de la DLL de contrôles communs Windows que l’application doit utiliser :

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

Pour une application Windows XP ou Windows Vista, la ressource de manifeste doit spécifier la version la plus récente des contrôles communs Windows pour l’application à utiliser. L’exemple ci-dessus utilise la version `6.0.0.0`, qui prend en charge la [contrôle Syslink](/windows/desktop/Controls/syslink-overview).

> [!NOTE]
> Vous ne pouvez avoir qu'une seule ressource de manifeste par module.

Pour afficher la version et tapez les informations contenues dans une ressource de manifeste, ouvrez le fichier dans une visionneuse XML ou de l’éditeur de texte Visual Studio. Si vous ouvrez une ressource de manifeste à partir de la fenêtre [Affichage des ressources](../windows/resource-view-window.md), la ressource s'ouvre au format binaire.

### <a name="to-open-a-manifest-resource"></a>Pour ouvrir une ressource de manifeste

1. Ouvrez votre projet dans Visual Studio et accédez à **l’Explorateur de solutions**.

1. Développez le **fichiers de ressources** dossier, puis :

   - Pour ouvrir dans l’éditeur de texte, double-cliquez sur le *.manifest* fichier.

   - Pour ouvrir dans un autre éditeur, cliquez sur le *.manifest* fichier et sélectionnez **ouvrir avec**. Spécifiez l’éditeur pour l’utiliser, puis sélectionnez **Open**.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Identificateurs de ressources (symboles)](../windows/symbols-resource-identifiers.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>