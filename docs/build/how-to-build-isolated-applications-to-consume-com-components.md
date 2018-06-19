---
title: 'Comment : générer des Applications isolées pour consommer des composants COM | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed2f43721eb698552ccde3e1b51ed4d6e467179
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367883"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Comment : générer des applications isolées pour consommer des composants COM
Applications isolées sont des applications qui ont des manifestes générés dans le programme. Vous pouvez créer des applications isolées pour consommer des composants COM.  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Pour ajouter des références COM aux manifestes d’applications isolées  
  
1.  Ouvrez les pages de propriétés de projet d’application isolée.  
  
2.  Développez le **propriétés de Configuration** nœud, puis développez le **outil manifeste** nœud.  
  
3.  Sélectionnez le **COM isolé** page de propriétés et définissez la **nom de fichier de composant** nom à la propriété du composant COM que vous souhaitez que l’application isolée pour consommer.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-build-manifests-into-isolated-applications"></a>Pour générer des manifestes dans des applications isolées  
  
1.  Ouvrez les pages de propriétés de projet d’application isolée.  
  
2.  Développez le **propriétés de Configuration** nœud, puis développez le **outil manifeste** nœud.  
  
3.  Sélectionnez le **d’entrée et sortie** page de propriétés et définissez la **incorporer le manifeste** propriété égale à **Oui**.  
  
4.  Cliquez sur **OK**.  
  
5.  Générez la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications isolées](http://msdn.microsoft.com/library/aa375190)   
 [À propos des assemblys côte à côte](http://msdn.microsoft.com/library/ff951640)