---
title: / APPCONTAINER (application de UWP/Microsoft Store) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eab6a9bd8ac37dec250739e3554c370726dce9eb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589575"
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
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le nœud **Propriétés de configuration**.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **ligne de commande** page de propriétés.  
  
5.  Dans **des Options supplémentaires**, entrez `/APPCONTAINER` ou `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)