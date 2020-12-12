---
description: En savoir plus sur:/APPCONTAINER (application Microsoft Store)
title: /APPCONTAINER (application UWP/Microsoft Store)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: 4cb78c85aa59ebd7fc0eb82af9497606bc3c431c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179575"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER (application Microsoft Store)

Spécifie si l’éditeur de liens crée une image exécutable qui doit être exécutée dans un conteneur d’application.

## <a name="syntax"></a>Syntaxe

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Notes

Par défaut,/APPCONTAINER est désactivé.

Cette option modifie un exécutable pour indiquer si l’application doit être exécutée dans l’environnement d’isolation du processus appcontainer. Spécifiez/APPCONTAINER pour une application qui doit s’exécuter dans l’environnement APPCONTAINER, par exemple, une plateforme Windows universelle (UWP) ou Windows Phone application 8. x. (L’option est définie automatiquement dans Visual Studio lorsque vous créez une application Windows universelle à partir d’un modèle.) Pour une application de bureau, spécifiez/APPCONTAINER : NO ou omettez simplement l’option.

L’option/APPCONTAINER a été introduite dans Windows 8.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Dans **options supplémentaires**, entrez `/APPCONTAINER` ou `/APPCONTAINER:NO` .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
