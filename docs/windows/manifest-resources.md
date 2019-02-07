---
title: Ressources de manifeste (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 2d135cb2d512313f107eef7e95ec90d7972b68b4
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850188"
---
# <a name="manifest-resources-c"></a>Ressources de manifeste (C++)

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

Pour une application Windows XP ou Windows Vista, la ressource de manifeste indique non seulement que l’application utilise la toute dernière version des contrôles communs Windows (v6.0, comme indiqué ci-dessus) mais qu’elle prend également en charge le nouveau [contrôle Syslink](/windows/desktop/Controls/syslink-overview).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

Pour afficher la version et tapez les informations contenues dans une ressource de manifeste, vous pouvez ouvrir le fichier dans une visionneuse XML ou dans l’éditeur de texte Visual Studio. Si vous ouvrez une ressource de manifeste à partir de la fenêtre [Affichage des ressources](../windows/resource-view-window.md), la ressource s'ouvre au format binaire. Pour afficher le contenu d’une ressource de manifeste dans un format plus lisible, vous devez ouvrir la ressource à partir de **l’Explorateur de solutions**.

## <a name="to-open-a-manifest-resource-in-the-text-editor"></a>Pour ouvrir une ressource de manifeste dans l'éditeur de texte

1. Votre projet étant ouvert dans **l’Explorateur de solutions**, développez le **fichiers de ressources** dossier.

1. Double-cliquez sur le fichier .manifest.

   Votre ressource de manifeste s’ouvre dans le **éditeur de texte**.

## <a name="to-open-a-manifest-resource-in-another-editor"></a>Pour ouvrir une ressource de manifeste dans un autre éditeur

1. Dans **l’Explorateur de solutions**, cliquez sur le fichier .manifest et choisissez **ouvrir avec...**  dans le menu contextuel.

1. Dans le **ouvrir avec** boîte de dialogue, spécifiez l’éditeur que vous souhaitez utiliser, puis sélectionnez **Open**.

## <a name="limitations"></a>Limitations

Vous ne pouvez avoir qu'une seule ressource de manifeste par module.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)<br/>
[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)