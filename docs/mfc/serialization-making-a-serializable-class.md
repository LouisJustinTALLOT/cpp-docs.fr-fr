---
description: 'En savoir plus sur : sérialisation : création d’une classe sérialisable'
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
ms.openlocfilehash: 21c45887199768094953066818acfe1b87d8d45d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217534"
---
# <a name="serialization-making-a-serializable-class"></a>Sérialisation : définir une classe sérialisable

Cinq étapes principales sont requises pour rendre une classe sérialisable. Elles sont répertoriées ci-dessous et expliquées dans les sections suivantes :

1. [Dériver votre classe de CObject](#_core_deriving_your_class_from_cobject) (ou d’une classe dérivée de `CObject` ).

1. [Substitution de la fonction membre Serialize](#_core_overriding_the_serialize_member_function).

1. [À l’aide de la macro DECLARE_SERIAL](#_core_using_the_declare_serial_macro) dans la déclaration de classe.

1. [Définition d’un constructeur qui ne prend pas d’arguments](#_core_defining_a_constructor_with_no_arguments).

1. [À l’aide de la macro IMPLEMENT_SERIAL dans le fichier d’implémentation](#_core_using_the_implement_serial_macro_in_the_implementation_file) de votre classe.

Si vous appelez `Serialize` directement plutôt que par le biais des opérateurs >> et << de [CArchive](../mfc/reference/carchive-class.md), les trois dernières étapes ne sont pas requises pour la sérialisation.

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a> Dérivation de votre classe de CObject

Le protocole et les fonctionnalités de base de sérialisation sont définis dans la classe `CObject`. En faisant dériver votre classe de `CObject` (ou une classe dérivée de `CObject`), comme indiqué dans la déclaration suivante de la classe `CPerson`, vous accédez au protocole de sérialisation et à la fonctionnalité `CObject`.

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a> Substitution de la fonction membre Serialize

La fonction membre `Serialize`, définie dans la classe `CObject`, est chargée de la sérialisation réelle des données nécessaires pour capturer l'état actuel d'un objet. La fonction `Serialize` a un argument `CArchive` qu’elle utilise pour lire et écrire les données de l’objet. L’objet [CArchive](../mfc/reference/carchive-class.md) possède une fonction membre, `IsStoring` , qui indique si le `Serialize` stocke (écriture de données) ou le chargement (lecture des données). En utilisant les résultats de `IsStoring` comme guide, vous insérez les données de votre objet dans l' `CArchive` objet à l’aide de l’opérateur d’insertion ( **<\<**) or extract data with the extraction operator (**>>** ).

Prenons l’exemple d’une classe dérivée de `CObject` et ayant deux nouvelles variables membres, de types `CString` et **Word**. Le fragment de déclaration de classe présente les variables membres et la déclaration de la fonction membre substituée de `Serialize` :

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Pour remplacer la fonction membre Serialize.

1. Appelez votre version de la classe de base de `Serialize` pour vérifier que la partie héritée de l'objet est sérialisée.

1. Insérez ou extrayez les variables membres spécifiques à votre classe.

   Les opérateurs d'insertion et d'extraction interagissent avec la classe d'archive pour lire et écrire les données. L'exemple suivant montre comment implémenter `Serialize` pour la classe `CPerson` déclarée ci-dessus :

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

Vous pouvez également utiliser les fonctions membres [CArchive :: Read](../mfc/reference/carchive-class.md#read) et [CArchive :: Write](../mfc/reference/carchive-class.md#write) pour lire et écrire de grandes quantités de données non typées.

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a> Utilisation de la macro DECLARE_SERIAL

La macro DECLARE_SERIAL est requise dans la déclaration des classes qui prendront en charge la sérialisation, comme illustré ici :

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a> Définition d’un constructeur sans argument

MFC requiert un constructeur par défaut lorsqu'il recrée les objets tels qu'ils sont désérialisés (chargés du disque). Le processus de désérialisation complète toutes les variables membres avec les valeurs requises pour recréer l’objet.

Ce constructeur peut être déclaré public, protégé ou privé. Si vous le protégez ou le rendez privé, vous vous assurez qu'il sera utilisé uniquement par les fonctions de sérialisation. Le constructeur doit mettre l'objet dans un état qui l'autorise à être supprimé, si nécessaire.

> [!NOTE]
> Si vous oubliez de définir un constructeur sans arguments dans une classe qui utilise les macros DECLARE_SERIAL et IMPLEMENT_SERIAL, vous obtiendrez un avertissement de compilateur « aucun constructeur par défaut disponible » sur la ligne où la macro IMPLEMENT_SERIAL est utilisée.

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> Utilisation de la macro IMPLEMENT_SERIAL dans le fichier d’implémentation

La macro IMPLEMENT_SERIAL est utilisée pour définir les différentes fonctions nécessaires à la dérivation d’une classe sérialisable à partir de `CObject` . Utilisez la macro du fichier d'implémentation (.CPP) pour la classe. Les deux premiers arguments à la macro sont le nom de la classe et le nom de la classe de base immédiate.

Le troisième argument de la macro est un numéro de schéma. Le numéro de schéma est essentiellement le numéro de version des objets de la classe. Utilisez un entier supérieur ou égal à 0 pour le numéro de schéma. (Ne confondez pas le numéro de schéma avec la terminologie de base de données.)

Le code de sérialisation MFC vérifie le numéro de schéma lors de la lecture des objets en mémoire. Si le numéro de schéma de l'objet sur le disque ne correspond pas au numéro de schéma de la classe en mémoire, la bibliothèque lèvera `CArchiveException`, ce qui empêchera votre programme de lire une version incorrecte de l'objet.

Si vous souhaitez que votre `Serialize` fonction membre puisse lire plusieurs versions, c’est-à-dire des fichiers écrits avec différentes versions de l’application, vous pouvez utiliser la valeur *VERSIONABLE_SCHEMA* en tant qu’argument de la macro IMPLEMENT_SERIAL. Pour les informations d'utilisation et un exemple, consultez la fonction membre `GetObjectSchema` de la classe `CArchive`.

L’exemple suivant montre comment utiliser IMPLEMENT_SERIAL pour une classe, `CPerson` , dérivée de `CObject` :

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Une fois que vous avez une classe sérialisable, vous pouvez sérialiser les objets de la classe, comme indiqué dans l’article [sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Voir aussi

[Sérialisation](../mfc/serialization-in-mfc.md)
