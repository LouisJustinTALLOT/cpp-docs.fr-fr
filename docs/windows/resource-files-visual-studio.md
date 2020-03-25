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
ms.openlocfilehash: 087cd613fa0dfd9cb6e07ac47a6a38d63bba004e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167873"
---
# <a name="resource-files-c"></a>Fichiers de ressources (C++)

> [!NOTE]
> Comme les projets écrits dans les langages de programmation .NET managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de l’ **Explorateur de solutions**. Utilisez l' [éditeur d’images](../windows/image-editor-for-icons.md) et l' [Éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés.
>
> Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Le terme *fichier de ressources* peut faire référence à plusieurs types de fichiers, par exemple :

- Le fichier de script de ressources (.rc) d’un programme

- Un fichier de modèle de ressource (.rct)

- Ressource individuelle existante sous forme de fichier autonome. Ce type comprend une bitmap, une icône ou un fichier curseur référencé à partir d’un fichier. rc.

- Fichier d’en-tête généré par l’environnement de développement. Ce type comprend des `Resource.h`, qui sont référencés à partir d’un fichier. rc.

Les ressources qui se trouvent dans d’autres types de fichiers, comme les fichiers. exe,. dll et. res, sont appelées *ressources*.

Vous pouvez utiliser des *fichiers de ressources* et des *ressources* à partir de votre projet. Vous pouvez également travailler avec ceux qui ne font pas partie du projet actuel ou qui n’ont pas été créés en dehors de l’environnement de développement de Visual Studio. Vous pouvez par exemple :

- Travailler avec des fichiers de ressources imbriqués et inclus de manière conditionnelle

- Mettre à jour des ressources existantes ou les C++convertir en éléments visuels.

- Importer ou exporter des ressources graphiques vers ou à partir de votre fichier de ressources actif

- Inclure des identificateurs partagés ou en lecture seule  (symboles) qui ne peuvent pas être modifiés par l’environnement de développement

- Inclure des ressources dans votre fichier exécutable (. exe) qui n’ont pas besoin d’être modifiés (ou ne doivent pas être modifiés), telles que des ressources partagées entre plusieurs projets.

- Inclure des types de ressources non pris en charge par l’environnement de développement

Pour plus d’informations sur les ressources, consultez Comment [créer des ressources](../windows/how-to-create-a-resource-script-file.md), gérer des [ressources](../windows/how-to-copy-resources.md)et [inclure des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Ressources modifiables

Les types de fichiers suivants peuvent être ouverts pour modifier les ressources qu’ils contiennent :

| Nom de fichier | Description |
|---|---|
| .rc | Fichiers de script de ressources |
| .rct | Fichiers de modèle de ressource |
| .res | Fichiers de ressources |
| .resx | Fichiers de ressources managés |
| .exe | Fichiers exécutables |
| .dll | Fichiers de bibliothèque de liens dynamiques |
| .bmp, .ico, .dib, .cur | Fichiers bitmap, icône, barre d’outils et curseur |

Lors de la modification de ressources, l’environnement Visual Studio fonctionne avec et affecte les fichiers suivants :

| Nom de fichier | Description |
|---|---|
| Resource.h | Fichier d’en-tête généré par l’environnement de développement qui contient des définitions de symbole.<br/><br/>Incluez ce fichier dans le contrôle de code source. |
| Filename.aps | Version binaire du fichier de script de ressources actuel utilisé pour le chargement rapide.<br /><br /> Les éditeurs de ressources ne lisent pas directement les fichiers. RC ou Resource. h. Le compilateur de ressources les compile en fichiers. APS qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques.<br/><br/>Comme dans le cadre d’un processus de compilation normal, les informations qui ne sont pas symboliques, telles que les commentaires, sont ignorées pendant le processus de compilation.<br/><br/>Chaque fois que le fichier. APS n’est pas synchronisé avec le fichier. RC, le fichier. RC est régénéré. Par exemple, lorsque vous **Enregistrez**, l’éditeur de ressources remplace le fichier. RC et le fichier Resource. h. Toute modification apportée aux ressources reste incorporée dans le fichier. RC, mais les commentaires sont toujours perdus une fois le fichier. RC remplacé. Pour plus d’informations sur la façon de conserver des commentaires, consultez [inclure des ressources au moment](../windows/how-to-include-resources-at-compile-time.md)de la compilation.<br/><br/>En règle générale, vous ne devez pas inclure le fichier. APS dans le contrôle de code source. |
| .rc | Fichier de script de ressources qui contient le script des ressources de votre projet actif. Ce fichier est remplacé par le fichier .aps à chaque enregistrement.<br/><br/>Incluez ce fichier dans le contrôle de code source. |

## <a name="manifest-resources"></a>Ressources de manifeste

Dans C++ les projets de bureau, les ressources de manifeste sont des fichiers XML qui décrivent les dépendances qu’une application utilise. Par exemple, dans Visual Studio, ce fichier manifeste généré par l’Assistant MFC définit la version des dll de contrôle commun Windows que l’application doit utiliser :

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

Pour une application Windows XP ou Windows Vista, la ressource de manifeste doit spécifier la version la plus récente des contrôles communs Windows que l’application doit utiliser. L’exemple ci-dessus utilise la version `6.0.0.0`, qui prend en charge le [contrôle Syslink](/windows/win32/Controls/syslink-overview).

> [!NOTE]
> Vous ne pouvez avoir qu'une seule ressource de manifeste par module.

Pour afficher les informations de version et de type contenues dans une ressource de manifeste, ouvrez le fichier dans une visionneuse XML ou dans l’éditeur de texte Visual Studio. Si vous ouvrez une ressource de manifeste à partir de la fenêtre [Affichage des ressources](../windows/resource-view-window.md), la ressource s'ouvre au format binaire.

### <a name="to-open-a-manifest-resource"></a>Pour ouvrir une ressource de manifeste

1. Ouvrez votre projet dans Visual Studio et accédez à **Explorateur de solutions**.

1. Développez le dossier **fichiers de ressources** , puis :

   - Pour ouvrir dans l’éditeur de texte, double-cliquez sur le fichier *. manifest* .

   - Pour ouvrir dans un autre éditeur, cliquez avec le bouton droit sur le fichier *. manifest* , puis sélectionnez **Ouvrir avec**. Spécifiez l’éditeur à utiliser, puis sélectionnez **ouvrir**.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br/>
[Identificateurs de ressources (symboles)](../windows/symbols-resource-identifiers.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>
