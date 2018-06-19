---
title: Dérivation d’une classe de CObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d0b629617c1592387f3f959996fd3e9837242ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349355"
---
# <a name="deriving-a-class-from-cobject"></a>Dérivation d'une classe de CObject
Cet article décrit la procédure minimale à suivre pour dériver une classe à partir de [CObject](../mfc/reference/cobject-class.md). Autres `CObject` classe décrivent les étapes nécessaires pour tirer parti des spécifique `CObject` fonctionnalités, telles que la sérialisation et la prise en charge du débogage diagnostic.  
  
 Dans les discussions de `CObject`, les termes « fichier d’interface » et « fichier d’implémentation » sont fréquemment utilisées. Le fichier d’interface (souvent appelé le fichier d’en-tête, ou. H) contient la déclaration de classe et toutes les autres informations nécessaires à l’utilisation de la classe. Le fichier d’implémentation (ou). Fichier CPP) contient la définition de classe, ainsi que le code qui implémente les fonctions membres de classe. Par exemple, pour une classe nommée `CPerson`, vous créez généralement un fichier d’interface nommé PERSON. H et un fichier d’implémentation nommé PERSON. CPP. Toutefois, pour certaines petites classes qui ne seront pas partagés entre les applications, il est parfois plus facile de combiner l’interface et l’implémentation dans une seule. Fichier CPP.  
  
 Vous pouvez choisir à partir de quatre niveaux de fonctionnalité lorsque vous dérivez une classe de `CObject`:  
  
-   Fonctionnalités de base : aucune prise en charge pour la sérialisation ou des informations de classe d’exécution n’inclut la gestion de mémoire de diagnostic.  
  
-   Fonctionnalités de base et la prise en charge des informations de classe d’exécution.  
  
-   Fonctionnalités de base et la prise en charge pour la création dynamique et les informations de classe d’exécution.  
  
-   Fonctionnalités de base et la prise en charge des informations de classe d’exécution, la création dynamique et la sérialisation.  
  
 Les classes destinées à être réutilisées (celles qui vous servira ultérieurement des classes de base) doivent inclure au moins prise en charge de la classe d’exécution et de prise en charge de la sérialisation, si un besoin de sérialisation ultérieure.  
  
 Vous choisissez le niveau de fonctionnalité à l’aide de macros de déclaration et d’implémentation spécifiques dans la déclaration et l’implémentation des classes que vous dérivez de `CObject`.  
  
 Le tableau suivant montre la relation entre les macros utilisées pour prendre en charge la sérialisation et les informations d’exécution.  
  
### <a name="macros-used-for-serialization-and-run-time-information"></a>Macros utilisées pour la sérialisation et les informations d’exécution  
  
|Macro utilisé|CObject::IsKindOf|CRuntimeClass ::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|  
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|Base `CObject` fonctionnalités|Non|Non|Non|  
|`DECLARE_DYNAMIC`|Oui|Non|Non|  
|`DECLARE_DYNCREATE`|Oui|Oui|Non|  
|`DECLARE_SERIAL`|Oui|Oui|Oui|  
  
#### <a name="to-use-basic-cobject-functionality"></a>Pour utiliser les fonctionnalités CObject de base  
  
1.  Utilisez la syntaxe C++ normale pour dériver votre classe de `CObject` (ou à partir d’une classe dérivée de `CObject`).  
  
     L’exemple suivant illustre le cas le plus simple, la dérivation d’une classe à partir de `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]  
  
 Normalement, toutefois, vous souhaiterez remplacer certains de `CObject`de fonctions membres pour gérer les spécificités de votre nouvelle classe. Par exemple, vous souhaiterez généralement remplacer le `Dump` fonction de `CObject` pour fournir la sortie de débogage pour le contenu de votre classe. Pour plus d’informations sur la procédure de remplacement `Dump`, consultez l’article [Diagnostics : dump d’objets](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59). Vous pouvez également substituer la `AssertValid` fonction de `CObject` pour effectuer un test personnalisé pour valider la cohérence des données membres des objets de classe. Pour obtenir une description de la procédure de remplacement `AssertValid`, consultez [MFC ASSERT_VALID et CObject::AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6).  
  
 L’article [spécifiant les niveaux de fonctionnalité](../mfc/specifying-levels-of-functionality.md) explique comment spécifier d’autres niveaux de fonctionnalité, y compris les informations de classe d’exécution, la création d’objet dynamique et la sérialisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CObject](../mfc/using-cobject.md)

