---
title: "TN002 : format des données d'objets persistants"
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 1880d5d43055966dea8ab16dc4f26bd4e4602ec5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447130"
---
# <a name="tn002-persistent-object-data-format"></a>TN002 : format des données d'objets persistants

Cette note décrit les routines MFC qui prennent en C++ charge les objets persistants et le format des données d’objet lorsqu’elles sont stockées dans un fichier. Cela s’applique uniquement aux classes avec les macros [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) .

## <a name="the-problem"></a>Le problème

L’implémentation MFC pour les données persistantes stocke des données pour de nombreux objets dans une seule partie contiguë d’un fichier. La méthode `Serialize` de l’objet traduit les données de l’objet en un format binaire compact.

L’implémentation garantit que toutes les données sont enregistrées dans le même format à l’aide de la [classe CArchive](../mfc/reference/carchive-class.md). Elle utilise un objet `CArchive` en tant que traducteur. Cet objet persiste à partir du moment où il est créé jusqu’à ce que vous appeliez [CArchive :: Close](../mfc/reference/carchive-class.md#close). Cette méthode peut être appelée explicitement par le programmeur ou implicitement par le destructeur lorsque le programme quitte l’étendue qui contient la `CArchive`.

Cette note décrit l’implémentation des membres `CArchive` [CArchive :: ReadObject](../mfc/reference/carchive-class.md#readobject) et [CArchive :: WriteObject](../mfc/reference/carchive-class.md#writeobject). Vous trouverez le code de ces fonctions dans Arcobj. cpp, ainsi que l’implémentation principale de `CArchive` dans Arccore. cpp. Le code utilisateur n’appelle pas `ReadObject` et `WriteObject` directement. Au lieu de cela, ces objets sont utilisés par les opérateurs d’insertion et d’extraction de type sécurisé spécifiques à la classe qui sont générés automatiquement par les macros DECLARE_SERIAL et IMPLEMENT_SERIAL. Le code suivant montre comment `WriteObject` et `ReadObject` sont implicitement appelés :

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Enregistrement d’objets dans le magasin (CArchive :: WriteObject)

La méthode `CArchive::WriteObject` écrit des données d’en-tête utilisées pour reconstruire l’objet. Ces données se composent de deux parties : le type de l’objet et l’état de l’objet. Cette méthode est également responsable de la gestion de l’identité de l’objet en cours d’écriture, de sorte qu’une seule copie est enregistrée, quel que soit le nombre de pointeurs vers cet objet (y compris les pointeurs circulaires).

L’enregistrement (insertion) et la restauration (extraction) d’objets s’appuient sur plusieurs « constantes manifestes ». Il s’agit de valeurs stockées dans le fichier binaire et qui fournissent des informations importantes à l’archive (Notez que le préfixe « w » indique des quantités de 16 bits) :

|Tag|Description|
|---------|-----------------|
|wNullTag|Utilisé pour les pointeurs d’objet NULL (0).|
|wNewClassTag|Indique que la description de la classe qui suit est nouvelle dans ce contexte d’archivage (-1).|
|wOldClassTag|Indique que la classe de l’objet en cours de lecture a été vue dans ce contexte (0x8000).|

Lors du stockage d’objets, l’archive gère un [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (le *m_pStoreMap*) qui est un mappage d’un objet stocké à un identificateur persistant 32 bits (PID). Un PID est attribué à chaque objet unique et à chaque nom de classe unique qui est enregistré dans le contexte de l’archive. Ces PID sont remis de manière séquentielle à partir de 1. Ces PID n’ont aucune importance en dehors de l’étendue de l’archive et, en particulier, ne doivent pas être confondus avec les numéros d’enregistrement ou d’autres éléments d’identité.

Dans la classe `CArchive`, les PID sont 32 bits, mais ils sont écrits en 16 bits, sauf s’ils sont supérieurs à 0x7FFE. Les PID volumineux sont écrits sous la forme 0x7FFF suivi du PID 32 bits. Cela assure la compatibilité avec les projets créés dans les versions antérieures.

Lorsqu’une demande est effectuée pour enregistrer un objet dans une archive (généralement à l’aide de l’opérateur d’insertion global), une vérification est effectuée pour un pointeur [COBJECT](../mfc/reference/cobject-class.md) null. Si le pointeur est NULL, *wNullTag* est inséré dans le flux d’archive.

Si le pointeur n’est pas NULL et peut être sérialisé (la classe est une classe `DECLARE_SERIAL`), le code vérifie la *m_pStoreMap* pour voir si l’objet a déjà été enregistré. Si c’est le cas, le code insère le PID 32 bits associé à cet objet dans le flux d’archive.

Si l’objet n’a pas encore été enregistré, deux possibilités s’imposent : l’objet et le type exact (autrement dit, la classe) de l’objet sont nouveaux dans ce contexte d’archivage, ou l’objet est d’un type exact. Pour déterminer si le type a été vu, le code interroge le *m_pStoreMap* pour obtenir un objet [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) qui correspond à l’objet `CRuntimeClass` associé à l’objet en cours d’enregistrement. En cas de correspondance, `WriteObject` insère une balise qui est le `OR` binaire de *wOldClassTag* et cet index. Si le `CRuntimeClass` est nouveau dans ce contexte d’archivage, `WriteObject` affecte un nouveau PID à cette classe et l’insère dans l’archive, précédée de la valeur *wNewClassTag* .

Le descripteur de cette classe est ensuite inséré dans l’archive à l’aide de la méthode `CRuntimeClass::Store`. `CRuntimeClass::Store` insère le numéro de schéma de la classe (voir ci-dessous) et le nom texte ASCII de la classe. Notez que l’utilisation du nom de texte ASCII ne garantit pas l’unicité de l’archive entre les applications. Par conséquent, vous devez baliser vos fichiers de données pour éviter toute altération. À la suite de l’insertion des informations de classe, l’archive place l’objet dans le *m_pStoreMap* puis appelle la méthode `Serialize` pour insérer des données spécifiques à la classe. Placer l’objet dans le *m_pStoreMap* avant d’appeler `Serialize` empêche l’enregistrement de plusieurs copies de l’objet dans le magasin.

Lors du retour à l’appelant initial (généralement la racine du réseau d’objets), vous devez appeler [CArchive :: Close](../mfc/reference/carchive-class.md#close). Si vous envisagez d’effectuer d’autres opérations [CFile](../mfc/reference/cfile-class.md), vous devez appeler la méthode `CArchive` [flush](../mfc/reference/carchive-class.md#flush) pour empêcher l’endommagement de l’archive.

> [!NOTE]
>  Cette implémentation impose une limite inconditionnelle d’index 0x3FFFFFFE par contexte d’archivage. Ce nombre représente le nombre maximal d’objets et de classes uniques qui peuvent être enregistrés dans une archive unique, mais un seul fichier de disque peut avoir un nombre illimité de contextes d’archive.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Chargement d’objets à partir du magasin (CArchive :: ReadObject)

Le chargement (extraction) d’objets utilise la méthode `CArchive::ReadObject` et est l’inverse de `WriteObject`. Comme avec `WriteObject`, `ReadObject` n’est pas appelé directement par le code utilisateur ; le code utilisateur doit appeler l’opérateur d’extraction de type sécurisé qui appelle `ReadObject` avec le `CRuntimeClass`attendu. Cela garantit l’intégrité du type de l’opération d’extraction.

Étant donné que l’implémentation de `WriteObject` a affecté l’amélioration des PID, à partir de 1 (0 est prédéfini comme objet NULL), l’implémentation de `ReadObject` peut utiliser un tableau pour conserver l’état du contexte d’archivage. Lorsqu’un PID est lu à partir du magasin, si le PID est plus grand que la limite supérieure actuelle de la *m_pLoadArray*, `ReadObject` sait qu’un nouvel objet (ou une description de la classe) suit.

## <a name="schema-numbers"></a>Numéros de schéma

Le numéro de schéma, qui est assigné à la classe lorsque la méthode `IMPLEMENT_SERIAL` de la classe est rencontrée, est la « version » de l’implémentation de la classe. Le schéma fait référence à l’implémentation de la classe, et non au nombre de fois où un objet donné a été rendu persistant (généralement appelé version d’objet).

Si vous envisagez de conserver plusieurs implémentations différentes de la même classe au fil du temps, l’incrémentation du schéma lorsque vous révisez l’implémentation de la méthode `Serialize` de votre objet vous permet d’écrire du code capable de charger des objets stockés à l’aide de versions antérieures de l’implémentation.

La méthode `CArchive::ReadObject` lèvera un [CArchiveException](../mfc/reference/carchiveexception-class.md) lorsqu’il rencontre un numéro de schéma dans le magasin persistant qui diffère du numéro de schéma de la description de la classe dans la mémoire. Il n’est pas facile de récupérer à partir de cette exception.

Vous pouvez utiliser `VERSIONABLE_SCHEMA` combiné avec (au niveau du bit **ou**) votre version de schéma pour empêcher la levée de cette exception. En utilisant `VERSIONABLE_SCHEMA`, votre code peut prendre l’action appropriée dans sa fonction `Serialize` en vérifiant la valeur de retour de [CArchive :: GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Appel direct de Serialize

Dans de nombreux cas, la surcharge du schéma d’archive des objets généraux de `WriteObject` et `ReadObject` n’est pas nécessaire. Il s’agit du scénario courant de sérialisation des données dans un [CDocument](../mfc/reference/cdocument-class.md). Dans ce cas, la méthode `Serialize` de la `CDocument` est appelée directement, et non avec les opérateurs d’extraction ou d’insertion. Le contenu du document peut à son tour utiliser le schéma d’archive d’objets le plus général.

L’appel de `Serialize` a les avantages et inconvénients suivants :

- Aucun octet supplémentaire n’est ajouté à l’archive avant ou après la sérialisation de l’objet. Non seulement les données enregistrées sont réduites, mais vous permet d’implémenter des routines de `Serialize` qui peuvent gérer n’importe quel format de fichier.

- Les MFC sont paramétrées afin que les implémentations `WriteObject` et `ReadObject` et les collections associées ne soient pas liées à votre application, sauf si vous avez besoin du schéma d’archive d’objets plus général à d’autres fins.

- Votre code n’a pas besoin de récupérer à partir des anciens numéros de schéma. Ainsi, votre code de sérialisation de document est responsable de l’encodage des numéros de schéma, des numéros de version de format de fichier ou des numéros d’identification que vous utilisez au début de vos fichiers de données.

- Tout objet sérialisé avec un appel direct à `Serialize` ne doit pas utiliser `CArchive::GetObjectSchema` ou doit gérer une valeur de retour (UINT)-1 indiquant que la version est inconnue.

Étant donné que `Serialize` est appelé directement sur votre document, il n’est généralement pas possible que les sous-objets du document archivent les références à leur document parent. Vous devez attribuer explicitement un pointeur vers son document conteneur à ces objets, ou vous devez utiliser la fonction [CArchive :: MapObject](../mfc/reference/carchive-class.md#mapobject) pour mapper le pointeur `CDocument` à un PID avant que ces pointeurs de retour ne soient archivés.

Comme indiqué précédemment, vous devez encoder les informations de version et de classe vous-même lorsque vous appelez `Serialize` directement, ce qui vous permet de modifier le format ultérieurement tout en maintenant la compatibilité descendante avec les anciens fichiers. La fonction `CArchive::SerializeClass` peut être appelée explicitement avant de sérialiser directement un objet ou avant d’appeler une classe de base.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
