---
title: Dérivation d'une classe de CObject
ms.date: 11/04/2016
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
ms.openlocfilehash: 860af88512acb33ff3035b3a04609165953d80a8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446977"
---
# <a name="deriving-a-class-from-cobject"></a>Dérivation d'une classe de CObject

Cet article décrit les étapes minimales nécessaires pour dériver une classe de [CObject](../mfc/reference/cobject-class.md). D’autres Articles de la classe `CObject` décrivent les étapes nécessaires pour tirer parti de fonctionnalités `CObject` spécifiques, telles que la prise en charge du débogage de la sérialisation et du diagnostic.

Dans les discussions de `CObject`, les termes « fichier d’interface » et « fichier d’implémentation » sont fréquemment utilisés. Fichier d’interface (souvent appelé fichier d’en-tête ou. H) contient la déclaration de classe et toutes les autres informations nécessaires à l’utilisation de la classe. Fichier d’implémentation (ou. CPP) contient la définition de classe ainsi que le code qui implémente les fonctions membres de classe. Par exemple, pour une classe nommée `CPerson`, vous créez généralement un fichier d’interface nommé PERSON. H et un fichier d’implémentation nommé PERSON. Cotisations. Toutefois, pour certaines petites classes qui ne seront pas partagées entre les applications, il est parfois plus facile de combiner l’interface et l’implémentation en une seule. Fichier CPP.

Vous pouvez choisir parmi quatre niveaux de fonctionnalités lors de la dérivation d’une classe à partir d' `CObject`:

- Fonctionnalités de base : aucune prise en charge des informations de classe d’exécution ou de la sérialisation, mais elle comprend la gestion de la mémoire de diagnostic.

- Fonctionnalités de base et prise en charge des informations de classe au moment de l’exécution.

- Fonctionnalités de base et prise en charge des informations de classe au moment de l’exécution et de la création dynamique.

- Fonctionnalités de base et prise en charge des informations de classe au moment de l’exécution, de la création dynamique et de la sérialisation.

Les classes conçues pour être réutilisées (celles qui seront par la suite utilisées comme classes de base) doivent au moins inclure la prise en charge de la classe d’exécution et la prise en charge de la sérialisation, si un futur besoin de sérialisation est attendu.

Vous choisissez le niveau de fonctionnalité en utilisant des macros de déclaration et d’implémentation spécifiques dans la déclaration et l’implémentation des classes que vous dérivez de `CObject`.

Le tableau suivant montre la relation entre les macros utilisées pour prendre en charge la sérialisation et les informations d’exécution.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Macros utilisées pour les informations de sérialisation et d’exécution

|Macro utilisée|CObject::IsKindOf|CRuntimeClass ::<br /><br /> CreateObject|CArchive :: operator > ><br /><br /> CArchive :: Operator < <|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Fonctionnalités de base de `CObject`|Non|Non|Non|
|`DECLARE_DYNAMIC`|Oui|Non|Non|
|`DECLARE_DYNCREATE`|Oui|Oui|Non|
|`DECLARE_SERIAL`|Oui|Oui|Oui|

#### <a name="to-use-basic-cobject-functionality"></a>Pour utiliser la fonctionnalité CObject de base

1. Utilisez la syntaxe C++ normale pour dériver votre classe de `CObject` (ou d’une classe dérivée de `CObject`).

   L’exemple suivant montre le cas le plus simple, la dérivation d’une classe à partir d' `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

En règle générale, toutefois, vous pouvez être amené à substituer certaines des fonctions membres de `CObject`pour gérer les détails de votre nouvelle classe. Par exemple, vous souhaiterez peut-être remplacer la fonction `Dump` de `CObject` pour fournir une sortie de débogage pour le contenu de votre classe. Pour plus d’informations sur la façon de substituer des `Dump`, consultez l’article [Personnalisation du dump d’objets](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100)). Vous pouvez également remplacer la fonction `AssertValid` de `CObject` pour fournir des tests personnalisés afin de valider la cohérence des données membres des objets de classe. Pour obtenir une description de la façon de substituer des `AssertValid`, consultez [MFC ASSERT_VALID et CObject :: AssertValid](reference/diagnostic-services.md#assert_valid).

L’article [spécification des niveaux de fonctionnalité](../mfc/specifying-levels-of-functionality.md) décrit comment spécifier d’autres niveaux de fonctionnalité, y compris les informations de classe d’exécution, la création d’objets dynamiques et la sérialisation.

## <a name="see-also"></a>Voir aussi

[Utilisation de CObject](../mfc/using-cobject.md)
