---
title: "-WHOLEARCHIVE (inclure tous les fichiers d’objets de bibliothèque) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed12541eeb0c85b2d218a7a5f3305413d4dc2ec8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE (inclure tous les fichiers d’objets de bibliothèque)
Force l’éditeur de liens à inclure tous les fichiers d’objet dans la bibliothèque statique dans le fichier exécutable associé.  
  
## <a name="syntax"></a>Syntaxe  
  
> / WHOLEARCHIVE [ :*bibliothèque*]  
  
## <a name="remarks"></a>Remarques  
  
L’option /WHOLEARCHIVE force l’éditeur de liens à inclure tous les fichiers à partir de l’objet une bibliothèque statique spécifiée, ou si aucune bibliothèque n’est spécifié, à partir de toutes les bibliothèques statiques spécifiées pour le lien de commande. Pour spécifier l’option /WHOLEARCHIVE pour plusieurs bibliothèques, vous pouvez utiliser plusieurs /WHOLEARCHIVE basculer sur la ligne de commande de l’éditeur de liens. Par défaut, l’éditeur de liens inclut les fichiers de l’objet dans la sortie liée uniquement si elles exportent les symboles référencés par d’autres fichiers de l’objet dans le fichier exécutable. L’option /WHOLEARCHIVE permet à l’éditeur de liens de traiter tous les fichiers d’objet archivées dans une bibliothèque statique comme s’ils ont été spécifiés individuellement sur la ligne de commande de l’éditeur de liens.  
  
L’option de /WHOLEARCHIVE peut être utilisée pour exporter de nouveau tous les symboles à partir d’une bibliothèque statique. Cela vous permet de vous assurer que toutes les ressources, votre code de bibliothèque et les métadonnées sont inclus lorsque vous créez un composant à partir de plusieurs bibliothèques statiques. Si vous voyez l’avertissement LNK4264 lorsque vous créez une bibliothèque statique qui contient des composants Windows Runtime pour l’exportation, utilisez l’option /WHOLEARCHIVE lors de la liaison de cette bibliothèque dans un autre composant ou application.  
  
L’option /WHOLEARCHIVE a été introduite dans Visual Studio 2015 Update 2.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
1.  Sélectionnez le **ligne de commande** page de propriétés **propriétés de Configuration**, **l’éditeur de liens**.  
  
1.  Ajoutez l’option /WHOLEARCHIVE à la **des Options supplémentaires** zone de texte.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)