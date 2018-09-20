---
title: 'TN002 : Format des données objet persistant | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a23ade068fa0d71715a76d3a99a393cc5458947c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399962"
---
# <a name="tn002-persistent-object-data-format"></a>TN002 : format des données d'objets persistants

Cette note décrit les routines MFC qui prennent en charge les objets C++ persistants et le format des données d’objet lorsqu’elle est stockée dans un fichier. Cela s’applique uniquement aux classes avec le [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) macros.

## <a name="the-problem"></a>Le problème

L’implémentation MFC pour les données persistantes stocke les données pour de nombreux objets dans une seule partie contiguë d’un fichier. L’objet `Serialize` méthode se traduit par des données de l’objet dans un format binaire compact.

L’implémentation garantit que toutes les données est enregistré dans le même format à l’aide de la [de la classe CArchive](../mfc/reference/carchive-class.md). Il utilise un `CArchive` objet comme un traducteur. Cet objet persiste à partir du moment de sa création jusqu'à ce que vous appeliez [CArchive::Close](../mfc/reference/carchive-class.md#close). Cette méthode peut être appelée explicitement par le programmeur ou implicitement par le destructeur quand le programme s’arrête l’étendue qui contient le `CArchive`.

Cette note décrit l’implémentation de la `CArchive` membres [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) et [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Vous trouverez le code pour ces fonctions dans Arcobj.cpp et l’implémentation principale pour `CArchive` dans Arccore.cpp. Code utilisateur n’appelle pas `ReadObject` et `WriteObject` directement. Au lieu de cela, ces objets sont utilisés par les opérateurs d’insertion et l’extraction de type sécurisé spécifique à la classe qui sont générés automatiquement par les macros DECLARE_SERIAL et IMPLEMENT_SERIAL. Le code suivant montre comment `WriteObject` et `ReadObject` sont appelées implicitement :

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>L’enregistrement des objets dans le Store (CArchive::WriteObject)

La méthode `CArchive::WriteObject` écrit les données d’en-tête qui sont utilisées pour reconstruire l’objet. Ces données se composent de deux parties : le type de l’objet et l’état de l’objet. Cette méthode est également responsable de l’identité de l’objet qui est écrite, afin qu’une seule copie est enregistrée, quel que soit le nombre de pointeurs vers cet objet (y compris les pointeurs circulaires).

L’enregistrement (insertion) et la restauration d’objets (extraction) s’appuie sur plusieurs « constantes manifestes ». Il s’agit des valeurs qui sont stockés au format binaire et fournissent des informations importantes à l’archive (Notez le préfixe « w » indique les quantités de 16 bits) :

|Balise|Description|
|---------|-----------------|
|wNullTag|Utilisé pour les pointeurs d’objet NULL (0).|
|wNewClassTag|Indique la description de la classe qui suit est une nouveauté de ce contexte d’archive (-1).|
|wOldClassTag|Indique la classe de l’objet en cours de lecture a été vu dans ce contexte (0 x 8000).|

Lorsque vous stockez des objets, l’archive conserve un [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (le *m_pStoreMap*) qui est un mappage à partir d’un objet stocké à un identificateur persistant de 32 bits (PID). Un PID est affecté à chaque objet unique et chaque nom de classe unique qui est enregistré dans le contexte de l’archive. Ces PID traitées séquentiellement, en commençant à 1. Ces PID n’ont aucune signification en dehors de l’étendue de l’archive et, en particulier, est à ne pas confondre avec les numéros d’enregistrement ou d’autres éléments de l’identité.

Dans la `CArchive` classe, PID est 32 bits, mais ils sont écrits en tant que 16 bits, sauf si elles sont supérieures à 0x7FFE. PID de grande taille est écrites comme 0x7FFF suivi par le PID de 32 bits. Cela maintient la compatibilité avec les projets qui ont été créés dans les versions antérieures.

Lorsqu’une demande est faite pour enregistrer un objet dans une archive (généralement en utilisant l’opérateur d’insertion globaux), une vérification est effectuée pour une valeur NULL [CObject](../mfc/reference/cobject-class.md) pointeur. Si le pointeur est NULL, le *wNullTag* est inséré dans le flux d’archive.

Si le pointeur n’est pas NULL et qu’il peut être sérialisé (la classe est un `DECLARE_SERIAL` classe), le code vérifie les *m_pStoreMap* pour voir si l’objet a déjà été enregistré. S’il a, le code insère le PID de 32 bits associé à cet objet dans le flux d’archive.

Si l’objet n’a pas été enregistré, il existe deux possibilités à prendre en compte : l’objet et le type exact (autrement dit, classe) de l’objet sont nouveaux pour ce contexte de l’archive, ou l’objet est d’un type exact déjà vu. Pour déterminer si le type a été vu, le code interroge le *m_pStoreMap* pour un [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objet qui correspond à la `CRuntimeClass` objet associé à l’objet en cours d’enregistrement. S’il existe une correspondance, `WriteObject` insère une balise qui est le bit par bit `OR` de *wOldClassTag* et cet index. Si le `CRuntimeClass` est une nouveauté de ce contexte de l’archive, `WriteObject` attribue un PID de nouveau à cette classe et l’insère dans l’archive, précédé par le *wNewClassTag* valeur.

Le descripteur de cette classe est ensuite inséré dans l’archive à l’aide de la `CRuntimeClass::Store` (méthode). `CRuntimeClass::Store` Insère le numéro de schéma de la classe (voir ci-dessous) et le nom de texte ASCII de la classe. Notez que l’utilisation du nom de texte ASCII ne garantit pas l’unicité de l’archive entre les applications. Par conséquent, vous balisez vos fichiers de données pour empêcher la corruption. Après l’insertion des informations de classe, l’archive place l’objet dans le *m_pStoreMap* , puis appelle la `Serialize` méthode pour insérer des données de classe spécifique. Placer l’objet dans le *m_pStoreMap* avant d’appeler `Serialize` empêche plusieurs copies de l’objet ne sont pas enregistrées dans le magasin.

Lors du retour à l’appelant initial (généralement la racine du réseau d’objets), vous devez appeler [CArchive::Close](../mfc/reference/carchive-class.md#close). Si vous envisagez d’effectuer d’autres [CFile](../mfc/reference/cfile-class.md)opérations, vous devez appeler la `CArchive` méthode [vider](../mfc/reference/carchive-class.md#flush) pour empêcher la corruption de l’archive.

> [!NOTE]
>  Cette implémentation n’impose une limite inconditionnelle d’indices 0x3FFFFFFE par contexte d’archivage. Ce nombre représente le nombre maximal d’objets uniques et des classes qui peuvent être enregistrées dans une archive unique, mais un seul fichier de disque peut avoir un nombre illimité de contextes d’archive.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Chargement d’objets à partir du Store (CArchive::ReadObject)

Le chargement (extraction) d’objets utilise les `CArchive::ReadObject` (méthode) et est l’inverse de `WriteObject`. Comme avec `WriteObject`, `ReadObject` n’est pas appelée directement par le code de l’utilisateur ; l’opérateur d’extraction de type sécurisé qui appelle le code utilisateur doit appeler `ReadObject` avec attendu `CRuntimeClass`. Cela garantit l’intégrité du type de l’opération d’extraction.

Dans la mesure où le `WriteObject` implémentation affecté PID croissant, en commençant par 1 (0 est prédéfini en tant que l’objet de valeur NULL), le `ReadObject` implémentation peut utiliser un tableau pour maintenir l’état du contexte d’archivage. Lorsque un PID est lu à partir du magasin, si le PID est supérieur à la limite supérieure en cours de la *m_pLoadArray*, `ReadObject` sait qu’un nouvel objet (ou la description de la classe) suit.

## <a name="schema-numbers"></a>Nombres de schéma

Le numéro de schéma, qui est affecté à la classe lors de la `IMPLEMENT_SERIAL` méthode de la classe est rencontrée, est la « version » de l’implémentation de classe. Le schéma fait référence à l’implémentation de la classe, pas au nombre de fois où un objet donné a été rendu persistant (généralement appelé la version de l’objet).

Si vous avez l’intention de gérer plusieurs implémentations différentes de la même classe dans le temps, incrémentant le schéma lors de la révision de votre objet `Serialize` implémentation de la méthode vous permettront d’écrire du code qui peut charger des objets stockés à l’aide de versions antérieures de l’implémentation.

Le `CArchive::ReadObject` méthode lève un [exception CArchiveException](../mfc/reference/carchiveexception-class.md) lorsqu’il rencontre un numéro de schéma dans le magasin persistant qui est différent du nombre de schéma de la description de la classe en mémoire. Il n’est pas facile de récupérer à partir de cette exception.

Vous pouvez utiliser `VERSIONABLE_SCHEMA` associé (au niveau du bit **ou**) votre version de schéma à conserver cette exception ne soit levée. À l’aide de `VERSIONABLE_SCHEMA`, votre code peut prendre les mesures appropriées dans son `Serialize` fonction en vérifiant la valeur de retour à partir de [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Appel sérialiser directement

Dans de nombreux cas, la surcharge du schéma général objet archive de `WriteObject` et `ReadObject` n’est pas nécessaire. C’est le cas courants de sérialiser les données dans un [CDocument](../mfc/reference/cdocument-class.md). Dans ce cas, le `Serialize` méthode de la `CDocument` est appelée directement, pas avec les opérateurs d’extraction ou insertion. Le contenu du document peut ensuite utiliser le schéma d’archive objet plus général.

L’appel `Serialize` a directement les avantages et inconvénients suivants :

- Aucun octet supplémentaires n’est ajoutés à l’archive avant ou après que l’objet est sérialisé. Cela rend les données enregistrées plus petits, non seulement mais vous permet d’implémenter `Serialize` routines qui peuvent gérer tous les formats de fichier.

- La bibliothèque MFC est réglée la `WriteObject` et `ReadObject` implémentations et les collections connexes ne seront pas liées à votre application, sauf si vous avez besoin du schéma d’archive objet plus général pour d’autres fins.

- Votre code n’a pas à récupérer à partir d’anciens numéros de schéma. Cela rend votre code de sérialisation de document responsable de l’encodage schéma nombres, numéros de version de format de fichier, ou quel que soit l’identification des numéros vous utiliser au début de vos fichiers de données.

- N’importe quel objet est sérialisé avec un appel direct à `Serialize` ne doivent pas utiliser `CArchive::GetObjectSchema` ou devez handle d’une valeur de retour de (UINT) -1 indiquant que la version est inconnue.

Étant donné que `Serialize` est appelé directement sur votre document, il est généralement pas possible pour les sous-objets du document pour archiver des références à leur document parent. Ces objets doivent être accordées un pointeur à son document conteneur explicitement ou vous devez utiliser [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) fonction permettant de mapper le `CDocument` pointeur vers un PID avant ces pointeurs arrière sont archivés.

Comme indiqué précédemment, vous devez encoder la version et informations de classe vous-même lorsque vous appelez `Serialize` directement, ce qui vous permet de modifier le format ultérieurement tout en conservant la compatibilité descendante avec les fichiers plus anciens. Le `CArchive::SerializeClass` fonction peut être appelée explicitement avant de sérialiser directement un objet ou avant d’appeler une classe de base.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

