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
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370440"
---
# <a name="tn002-persistent-object-data-format"></a>TN002 : format des données d'objets persistants

Cette note décrit les routines MFC qui prennent en charge les objets CMD persistants et le format des données de l’objet lorsqu’elles sont stockées dans un fichier. Cela ne s’applique qu’aux classes avec les [macros DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL.](../mfc/reference/run-time-object-model-services.md#implement_serial)

## <a name="the-problem"></a>Le problème

La mise en œuvre de MFC pour les données persistantes stocke des données pour de nombreux objets dans une seule partie contigu d’un fichier. La méthode `Serialize` de l’objet traduit les données de l’objet en un format binaire compact.

La mise en œuvre garantit que toutes les données sont enregistrées dans le même format en utilisant la [classe CArchive](../mfc/reference/carchive-class.md). Il utilise `CArchive` un objet comme traducteur. Cet objet persiste à partir du moment où il est créé jusqu’à ce que vous appelez [CArchive::Close](../mfc/reference/carchive-class.md#close). Cette méthode peut être appelée explicitement par le programmeur ou implicitement par le destructeur `CArchive`lorsque le programme quitte la portée qui contient le .

Cette note décrit la `CArchive` mise en œuvre des membres [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) et [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Vous trouverez le code pour ces fonctions dans Arcobj.cpp, et la mise en œuvre principale pour `CArchive` arccore.cpp. Le code utilisateur `ReadObject` `WriteObject` n’appelle pas et directement. Au lieu de cela, ces objets sont utilisés par des opérateurs d’insertion et d’extraction spécifiques à des classes qui sont générés automatiquement par les DECLARE_SERIAL et IMPLEMENT_SERIAL macros. Le code suivant `WriteObject` `ReadObject` montre comment et sont implicitement appelés:

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Enregistrer des objets dans le magasin (CArchive::WriteObject)

La `CArchive::WriteObject` méthode écrit des données d’en-tête qui sont utilisées pour reconstruire l’objet. Ces données se composent de deux parties : le type de l’objet et l’état de l’objet. Cette méthode est également responsable du maintien de l’identité de l’objet en cours d’écriture, de sorte que seule une seule copie est enregistrée, quel que soit le nombre de pointeurs à cet objet (y compris les pointeurs circulaires).

L’enregistrement (insérer) et la restauration (d’extraction) d’objets repose sur plusieurs « constantes manifestes ». Ce sont des valeurs qui sont stockées en binaire et fournissent des informations importantes à l’archive (notez que le préfixe "w" indique des quantités 16 bits):

|Tag|Description|
|---------|-----------------|
|wNullTag (en)|Utilisé pour les pointeurs d’objets NULL (0).|
|wNewClassTag (en)|Indique que la description de classe qui suit est nouvelle dans ce contexte d’archives (-1).|
|wOldClassTag (en)|Indique que la classe de l’objet lu a été vue dans ce contexte (0x8000).|

Lors du stockage d’objets, l’archive maintient un [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (le *m_pStoreMap*) qui est une cartographie à partir d’un objet stocké à un identificateur persistant 32 bits (PID). Une MIP est attribuée à chaque objet unique et à chaque nom de classe unique qui est enregistré dans le contexte de l’archive. Ces DIP sont distribués séquentiellement à partir de 1. Ces DIP n’ont aucune signification en dehors de la portée de l’archive et, en particulier, ne doivent pas être confondus avec des nombres records ou d’autres éléments d’identité.

Dans `CArchive` la classe, les PID sont 32 bits, mais ils sont écrits comme 16 bits à moins qu’ils ne soient plus grands que 0x7FFE. Les grands PID sont écrits sous forme de 0x7FFF suivis de la PID 32 bits. Cela maintient la compatibilité avec les projets qui ont été créés dans les versions antérieures.

Lorsqu’une demande est faite pour enregistrer un objet à une archive (généralement en utilisant l’opérateur d’insertion global), un contrôle est effectué pour un pointeur [NULL CObject.](../mfc/reference/cobject-class.md) Si le pointeur est NULL, le *wNullTag* est inséré dans le flux d’archives.

Si le pointeur n’est pas NULL et `DECLARE_SERIAL` peut être sérialisé (la classe est une classe), le code vérifie le *m_pStoreMap* pour voir si l’objet a déjà été enregistré. Si c’est le cas, le code insère la MIP 32 bits associée à cet objet dans le flux d’archives.

Si l’objet n’a pas été enregistré auparavant, il y a deux possibilités à considérer : soit l’objet et le type exact (c’est-à-dire, classe) de l’objet sont nouveaux dans ce contexte d’archive, soit l’objet est d’un type exact déjà vu. Pour déterminer si le type a été vu, le code interroge le *m_pStoreMap* pour `CRuntimeClass` un objet [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) qui correspond à l’objet associé à l’objet enregistré. S’il ya `WriteObject` une correspondance, insère une `OR` étiquette qui est le bit-sage de *wOldClassTag* et cet index. Si `CRuntimeClass` le nouveau dans ce `WriteObject` contexte d’archive, attribue une nouvelle PID à cette classe et l’insère dans l’archive, précédée par la valeur *wNewClassTag.*

Le descripteur de cette classe est ensuite `CRuntimeClass::Store` inséré dans l’archive en utilisant la méthode. `CRuntimeClass::Store`insère le numéro de schéma de la classe (voir ci-dessous) et le nom de texte ASCII de la classe. Notez que l’utilisation du nom de texte ASCII ne garantit pas un caractère unique de l’archive entre les applications. Par conséquent, vous devez marquer vos fichiers de données pour prévenir la corruption. Après l’insertion des informations de classe, l’archive met l’objet dans le *m_pStoreMap,* puis appelle la méthode pour insérer des données spécifiques à la `Serialize` classe. Placer l’objet *m_pStoreMap* dans le m_pStoreMap `Serialize` avant d’appeler empêche plusieurs copies de l’objet d’être enregistrées dans le magasin.

Lorsque vous retournez à l’appelant initial (généralement la racine du réseau d’objets), vous devez appeler [CArchive::Close](../mfc/reference/carchive-class.md#close). Si vous prévoyez d’effectuer d’autres opérations `CArchive` [CFile,](../mfc/reference/cfile-class.md)vous devez appeler la méthode [Flush](../mfc/reference/carchive-class.md#flush) pour prévenir la corruption de l’archive.

> [!NOTE]
> Cette mise en œuvre impose une limite dure de 0x3FFFFFFFFE indices par contexte d’archivage. Ce nombre représente le nombre maximum d’objets et de classes uniques qui peuvent être enregistrés dans une seule archive, mais un seul fichier de disque peut avoir un nombre illimité de contextes d’archive.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Chargement d’objets à partir du magasin (CArchive::ReadObject)

Le chargement (extrait) `CArchive::ReadObject` d’objets utilise `WriteObject`la méthode et est l’inverse de . Comme `WriteObject`avec `ReadObject` , n’est pas appelé directement par le code utilisateur; code utilisateur doit appeler l’opérateur `ReadObject` d’extraction `CRuntimeClass`de type-sûr qui appelle avec le prévu . Cela assure l’intégrité du type de l’extraction.

Étant `WriteObject` donné que la mise en œuvre assignée augmente les DIP, `ReadObject` à commencer par 1 (0 est prédéfinie comme l’objet NULL), la mise en œuvre peut utiliser un tableau pour maintenir l’état du contexte d’archives. Lorsqu’une MIP est lue à partir du magasin, si la MIP `ReadObject` est plus grande que la limite supérieure actuelle du *m_pLoadArray,* sait qu’un nouvel objet (ou description de classe) suit.

## <a name="schema-numbers"></a>Numéros Schema

Le numéro de schéma, qui est `IMPLEMENT_SERIAL` attribué à la classe lorsque la méthode de la classe est rencontrée, est la «version» de la mise en œuvre de la classe. Le schéma fait référence à la mise en œuvre de la classe, et non au nombre de fois qu’un objet donné a été rendu persistant (généralement appelé la version objet).

Si vous avez l’intention de maintenir plusieurs implémentations différentes de la même `Serialize` classe au fil du temps, l’augmentation du schéma que vous révisez la mise en œuvre de la méthode de votre objet vous permettra d’écrire du code qui peut charger des objets stockés en utilisant des versions plus anciennes de l’implémentation.

La `CArchive::ReadObject` méthode jettera un [CArchiveException](../mfc/reference/carchiveexception-class.md) quand il rencontre un numéro de schéma dans le magasin persistant qui diffère du nombre schéma de la description de classe dans la mémoire. Il n’est pas facile de se remettre de cette exception.

Vous pouvez `VERSIONABLE_SCHEMA` utiliser combiné avec (bitwise **OU**) votre version schéma pour empêcher cette exception d’être jeté. En `VERSIONABLE_SCHEMA`utilisant , votre code peut `Serialize` prendre les mesures appropriées dans sa fonction en vérifiant la valeur de retour de [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Appeler Serialize directement

Dans de nombreux cas, les frais `WriteObject` `ReadObject` généraux du schéma d’archivage de l’objet général et n’est pas nécessaire. C’est le cas courant de la sérialisation des données dans un [CDocument](../mfc/reference/cdocument-class.md). Dans ce cas, `Serialize` la `CDocument` méthode de la est appelée directement, pas avec l’extrait ou les opérateurs d’insertion. Le contenu du document peut à son tour utiliser le schéma d’archivage d’objets plus général.

L’appel `Serialize` a directement les avantages et les inconvénients suivants :

- Aucun octet supplémentaire n’est ajouté à l’archive avant ou après la sérialisation de l’objet. Cela permet non seulement de réduire les `Serialize` données enregistrées, mais vous permet de mettre en œuvre des routines qui peuvent gérer n’importe quel format de fichier.

- Le MFC est `WriteObject` réglé `ReadObject` de sorte que les implémentations et les collections connexes ne seront pas liés à votre application à moins que vous ayez besoin du schéma d’archivage d’objets plus général à d’autres fins.

- Votre code n’a pas à récupérer à partir de vieux numéros de schéma. Cela rend votre code de sérialisation de documents responsable de l’encodage des numéros de schéma, des numéros de version format de fichier ou des numéros d’identification que vous utilisez au début de vos fichiers de données.

- Tout objet qui est sérialisé avec un appel direct à `Serialize` ne doit pas utiliser `CArchive::GetObjectSchema` ou doit gérer une valeur de retour de (UINT)-1 indiquant que la version était inconnue.

Parce `Serialize` que l’on appelle directement sur votre document, il n’est généralement pas possible pour les sous-objets du document d’archiver les références à leur document parent. Ces objets doivent être donnés un pointeur à leur document de conteneur explicitement `CDocument` ou vous devez utiliser [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) fonction pour cartographier le pointeur à une MIP avant que ces pointeurs arrière sont archivés.

Comme indiqué précédemment, vous devez coder la version `Serialize` et les informations de classe vous-même lorsque vous appelez directement, vous permettant de modifier le format plus tard tout en maintenant la compatibilité vers l’arrière avec les fichiers plus anciens. La `CArchive::SerializeClass` fonction peut être appelée explicitement avant de sérialiser directement un objet ou avant d’appeler une classe de base.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
