---
title: Lecture des plages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8ebad4bfda77238ad8c861410e2af5453df73af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383642"
---
# <a name="reading-ranges"></a>Lecture des plages
**ANSI 4.9.6.2** L’interprétation d’un tiret (-) qui n’est ni le premier ni le dernier caractère de la scanlist pour la conversion % [ dans la fonction `fscanf`  
  
 La ligne suivante  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 lit tout nombre de caractères dans la plage A-Z dans la chaîne vers laquelle pointe `strptr`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions des bibliothèques](../c-language/library-functions.md)