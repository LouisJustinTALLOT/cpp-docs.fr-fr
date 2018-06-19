---
title: -ALLOWBIND | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af4a9f3d898d0087f0e8e861ccfe72e4adadb1de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368913"
---
# <a name="allowbind"></a>/ALLOWBIND
Spécifie si une DLL peut être liée.  
  
```  
  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 Le **/ALLOWBIND** option définit un bit dans l’en-tête d’une DLL qui indique à Bind.exe que l’image est autorisée à être liée. Liaison permettent à une image de chargement plus rapide lorsque le chargeur ne doit pas nécessairement redéfinir et effectuer la correction de l’adresse pour chaque DLL référencée. Vous souhaiterez peut-être éviter une DLL soit liée si elle a été signée numériquement, la liaison invalide la signature. Liaison n’a aucun effet si la randomisation du format d’espace d’adresse (ASLR) est activée pour l’image à l’aide de **/DYNAMICBASE** sur les versions de Windows qui prennent en charge ASLR.  
  
 Utilisez **/ALLOWBIND : no** pour empêcher la liaison de la DLL Bind.exe.  
  
 Pour plus d’informations, consultez la [/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) option de l’éditeur de liens.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)