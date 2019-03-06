---
title: / APPCONTAINER (application de UWP/Microsoft Store)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: c58559a908a9281507c74c2dd3ff7e56490cb6e3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418670"
---
# <a name="appcontainer-microsoft-store-app"></a>/ APPCONTAINER (application Microsoft Store)

Spécifie si l’éditeur de liens crée une image exécutable qui doit être exécutée dans un conteneur d’application.

## <a name="syntax"></a>Syntaxe

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Notes

Par défaut, /APPCONTAINER est désactivé.

Cette option modifie un fichier exécutable pour indiquer si l’application doit être exécutée dans l’environnement d’isolation des processus appcontainer. Spécifiez /APPCONTAINER pour une application qui doit s’exécuter dans l’environnement appcontainer — par exemple, une application 8.x Universal Windows Platform (UWP) ou Windows Phone. (L’option est définie automatiquement dans Visual Studio lorsque vous créez une application Windows universelle à partir d’un modèle.) Pour une application de bureau, spécifiez/appcontainer : no ou omettez simplement l’option.

L’option /APPCONTAINER a été introduite dans Windows 8.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Dans **des Options supplémentaires**, entrez `/APPCONTAINER` ou `/APPCONTAINER:NO`.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
