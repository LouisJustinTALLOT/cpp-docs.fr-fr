---
title: Dérivation d'une classe de CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
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
ms.openlocfilehash: e2c759dfd308beed0f04b8d8c2868abeeb1cfb45
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301244"
---
# <a name="deriving-a-class-from-cobject"></a>Dérivation d'une classe de CObject

Cet article décrit la procédure minimale nécessaire de dériver une classe à partir de [CObject](../mfc/reference/cobject-class.md). Autres `CObject` articles de la classe décrivent les étapes nécessaires pour tirer parti des spécifiques `CObject` fonctionnalités, telles que la sérialisation et la prise en charge du débogage diagnostic.

Dans les discussions de `CObject`, les termes « fichier d’interface » et « fichier d’implémentation » sont fréquemment utilisées. Le fichier d’interface (souvent appelé le fichier d’en-tête, ou. H) contient la déclaration de classe et toute autre information nécessaire pour utiliser la classe. Le fichier d’implémentation (ou). Fichier CPP) contient la définition de classe, ainsi que le code qui implémente les fonctions membres de classe. Par exemple, pour une classe nommée `CPerson`, vous créez généralement un fichier de l’interface nommé PERSON. H et un fichier d’implémentation nommé PERSON. CPP. Toutefois, pour certaines petites classes qui ne seront pas partagés entre les applications, il est parfois plus facile de combiner l’interface et l’implémentation dans une seule. Fichier CPP.

Vous pouvez choisir à partir de quatre niveaux de fonctionnalité lorsque vous dérivez une classe à partir de `CObject`:

- Fonctionnalités de base : Aucune prise en charge pour les informations de classe d’exécution ou de sérialisation n’inclut, mais la gestion de mémoire de diagnostic.

- Fonctionnalités de base et prise en charge des informations de classe d’exécution.

- Fonctionnalités de base et prise en charge des informations de classe d’exécution et la création dynamique.

- Fonctionnalités de base et prise en charge des informations de classe d’exécution, la création dynamique et la sérialisation.

Classes conçues pour être réutilisée (ceux qui vous servira ultérieurement des classes de base) doivent inclure au moins prise en charge de la classe d’exécution et de prise en charge de la sérialisation, si n’importe quel besoin de sérialisation ultérieure.

Vous choisissez le niveau de fonctionnalité à l’aide des macros de déclaration et d’implémentation spécifiques dans la déclaration et l’implémentation des classes que vous dérivez de `CObject`.

Le tableau suivant montre la relation entre les macros utilisées pour prendre en charge la sérialisation et les informations d’exécution.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Utilisé pour la sérialisation et des informations sur l’exécution des macros

|Macro utilisé|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator>><br /><br /> CArchive::operator <<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Base `CObject` fonctionnalités|Aucune|Non|Non|
|`DECLARE_DYNAMIC`|Oui|Non|Non|
|`DECLARE_DYNCREATE`|Oui|Oui|Non|
|`DECLARE_SERIAL`|Oui|Oui|Oui|

#### <a name="to-use-basic-cobject-functionality"></a>Pour utiliser les fonctionnalités CObject de base

1. Utilisez la syntaxe C++ normale pour dériver votre classe de `CObject` (ou à partir d’une classe dérivée de `CObject`).

   L’exemple suivant montre le cas le plus simple, la dérivation d’une classe à partir de `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Normalement, toutefois, vous voudrez peut-être substituer certaines des `CObject`de fonctions membres pour gérer les particularités de votre nouvelle classe. Par exemple, vous souhaiterez généralement remplacer le `Dump` fonction de `CObject` pour fournir la sortie de débogage pour le contenu de votre classe. Pour plus d’informations sur la procédure de remplacement `Dump`, consultez l’article [Diagnostics : Vider le contenu de l’objet](/previous-versions/visualstudio/visual-studio-2010/sc15kz85). Vous pouvez également substituer la `AssertValid` fonction de `CObject` pour effectuer un test personnalisé pour valider la cohérence des données membres des objets de classe. Pour obtenir une description de la procédure de remplacement `AssertValid`, consultez [MFC ASSERT_VALID et CObject::AssertValid](/previous-versions/visualstudio/visual-studio-2010/38z04tfa).

L’article [spécifiant les niveaux de fonctionnalité](../mfc/specifying-levels-of-functionality.md) explique comment spécifier d’autres niveaux de fonctionnalité, y compris les informations de classe d’exécution, la création d’objets dynamiques et la sérialisation.

## <a name="see-also"></a>Voir aussi

[Utilisation de CObject](../mfc/using-cobject.md)
