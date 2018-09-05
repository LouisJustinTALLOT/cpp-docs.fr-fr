---
title: Ressources de manifeste | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f06e2d430867d04600547312fbc484ec6257c53
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685150"
---
# <a name="manifest-resources"></a>Ressources de manifeste

Les ressources de manifeste sont des fichiers XML qui décrivent les dépendances qu'une application utilise. Par exemple, dans Visual Studio, le fichier manifeste généré par l'Assistant MFC définit la DLL de contrôle commun Windows que l'application doit utiliser, version 5.0 ou 6.0 :

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

Pour une application Windows XP ou Windows Vista, la ressource de manifeste indique non seulement que l’application utilise la version la plus récente des contrôles communs Windows (v6.0, comme indiqué ci-dessus) mais il prend également en charge la [contrôle Syslink](/windows/desktop/Controls/syslink-overview).

Pour afficher la version et tapez les informations contenues dans une ressource de manifeste, vous pouvez ouvrir le fichier dans une visionneuse XML ou dans l’éditeur de texte Visual Studio. Pour plus d'informations, voir [Ouverture d'une ressource de manifeste dans l'éditeur de texte Visual Studio](../windows/how-to-open-a-manifest-resource.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

## <a name="limitations"></a>Limitations

Vous ne pouvez avoir qu'une seule ressource de manifeste par module.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)  
[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)