---
title: 'Sérialisation : définir une classe sérialisable'
ms.date: 11/04/2016
helpviewer_keywords:
- serializable class [MFC]
- DECLARE_SERIAL macro [MFC]
- default constructor [MFC]
- VERSIONABLE_SCHEMA macro [MFC]
- classes [MFC], derived
- IMPLEMENT_SERIAL macro [MFC]
- no-arguments constructor [MFC]
- Serialize method, overriding
- defaults [MFC], constructor
- CObject class [MFC], deriving serializable classes
- constructors [MFC], defining with no arguments
- serialization [MFC], serializable classes
- no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
ms.openlocfilehash: 9648bd4f516a5f174534336b1ca3b42bb51ca0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372704"
---
# <a name="serialization-making-a-serializable-class"></a>Sérialisation : définir une classe sérialisable

Cinq étapes principales sont requises pour rendre une classe sérialisable. Elles sont répertoriées ci-dessous et expliquées dans les sections suivantes :

1. [Dépérir votre classe de CObject](#_core_deriving_your_class_from_cobject) (ou d’une classe dérivée de `CObject`).

1. [Dépassement de la fonction membre Serialize](#_core_overriding_the_serialize_member_function).

1. [Utilisation de la macro DECLARE_SERIAL](#_core_using_the_declare_serial_macro) dans la déclaration de classe.

1. [Définir un constructeur qui ne prend pas d’arguments](#_core_defining_a_constructor_with_no_arguments).

1. [Utilisation de la macro IMPLEMENT_SERIAL dans le fichier d’implémentation](#_core_using_the_implement_serial_macro_in_the_implementation_file) de votre classe.

Si vous `Serialize` appelez directement plutôt que par l’intermédiaire des opérateurs >> et << de [CArchive](../mfc/reference/carchive-class.md), les trois dernières étapes ne sont pas nécessaires pour la sérialisation.

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a>Dépérir votre classe de CObject

Le protocole et les fonctionnalités de base de sérialisation sont définis dans la classe `CObject`. En faisant dériver votre classe de `CObject` (ou une classe dérivée de `CObject`), comme indiqué dans la déclaration suivante de la classe `CPerson`, vous accédez au protocole de sérialisation et à la fonctionnalité `CObject`.

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a>Dépassement de la fonction de membre sérialisation

La fonction membre `Serialize`, définie dans la classe `CObject`, est chargée de la sérialisation réelle des données nécessaires pour capturer l'état actuel d'un objet. La fonction `Serialize` a un argument `CArchive` qu’elle utilise pour lire et écrire les données de l’objet. [L’objet CArchive](../mfc/reference/carchive-class.md) a `IsStoring`une fonction `Serialize` membre, qui indique s’il s’agit de stocker (écriture de données) ou de charger (données de lecture). En utilisant `IsStoring` les résultats de comme guide, soit vous `CArchive` insérez**<** les données de votre objet**>>** dans l’objet avec l’opérateur d’insertion ( ) ou extrairez des données avec l’opérateur d’extraction ( ).

Considérez une classe `CObject` qui est dérivée et `CString` a deux nouvelles variables de membre, des types et **WORD**. Le fragment de déclaration de classe présente les variables membres et la déclaration de la fonction membre substituée de `Serialize` :

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Pour remplacer la fonction membre Serialize.

1. Appelez votre version de la classe de base de `Serialize` pour vérifier que la partie héritée de l'objet est sérialisée.

1. Insérez ou extrayez les variables membres spécifiques à votre classe.

   Les opérateurs d'insertion et d'extraction interagissent avec la classe d'archive pour lire et écrire les données. L'exemple suivant montre comment implémenter `Serialize` pour la classe `CPerson` déclarée ci-dessus :

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

Vous pouvez également utiliser le [CArchive::Lire](../mfc/reference/carchive-class.md#read) et [CArchive::Écrire](../mfc/reference/carchive-class.md#write) des fonctions de membre pour lire et écrire de grandes quantités de données nontypées.

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a>Utilisation du DECLARE_SERIAL Macro

La macro DECLARE_SERIAL est requise dans la déclaration des classes qui soutiendra la sérialisation, comme indiqué ici:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a>Définir un constructeur sans arguments

MFC requiert un constructeur par défaut lorsqu'il recrée les objets tels qu'ils sont désérialisés (chargés du disque). Le processus de désérialisation complète toutes les variables membres avec les valeurs requises pour recréer l’objet.

Ce constructeur peut être déclaré public, protégé ou privé. Si vous le protégez ou le rendez privé, vous vous assurez qu'il sera utilisé uniquement par les fonctions de sérialisation. Le constructeur doit mettre l'objet dans un état qui l'autorise à être supprimé, si nécessaire.

> [!NOTE]
> Si vous oubliez de définir un constructeur sans arguments dans une classe qui utilise le DECLARE_SERIAL et IMPLEMENT_SERIAL macros, vous obtiendrez un "sans constructeur par défaut disponible" avertissement compilateur sur la ligne où le IMPLEMENT_SERIAL macro est utilisé.

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>Utilisation du IMPLEMENT_SERIAL Macro dans le fichier de mise en œuvre

La macro IMPLEMENT_SERIAL est utilisée pour définir les différentes fonctions nécessaires `CObject`lorsque vous dérivez une classe sérialisable de . Utilisez la macro du fichier d'implémentation (.CPP) pour la classe. Les deux premiers arguments à la macro sont le nom de la classe et le nom de la classe de base immédiate.

Le troisième argument de la macro est un numéro de schéma. Le numéro de schéma est essentiellement le numéro de version des objets de la classe. Utilisez un entier supérieur ou égal à 0 pour le numéro de schéma. (Ne confondez pas le numéro de schéma avec la terminologie de base de données.)

Le code de sérialisation MFC vérifie le numéro de schéma lors de la lecture des objets en mémoire. Si le numéro de schéma de l'objet sur le disque ne correspond pas au numéro de schéma de la classe en mémoire, la bibliothèque lèvera `CArchiveException`, ce qui empêchera votre programme de lire une version incorrecte de l'objet.

Si vous `Serialize` voulez que votre fonction de membre soit en mesure de lire plusieurs versions — c’est-à-dire les fichiers écrits avec différentes versions de l’application — vous pouvez utiliser la valeur *VERSIONABLE_SCHEMA* comme argument à la macro IMPLEMENT_SERIAL. Pour les informations d'utilisation et un exemple, consultez la fonction membre `GetObjectSchema` de la classe `CArchive`.

L’exemple suivant montre comment utiliser IMPLEMENT_SERIAL pour `CPerson`une classe, `CObject`qui est dérivé de :

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Une fois que vous avez une classe sérialisable, vous pouvez sérialiser des objets de la classe, comme discuté dans l’article [Serialization: Serializing an Object](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Voir aussi

[Sérialisation](../mfc/serialization-in-mfc.md)
