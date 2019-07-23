---
title: CArchive (classe)
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: 3cf5c3b7a79e846928b5a7ee0af12a3324e141a3
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376359"
---
# <a name="carchive-class"></a>CArchive (classe)

Vous permet d’enregistrer un réseau complexe d’objets sous une forme binaire permanente (généralement un stockage sur disque) qui persiste une fois ces objets supprimés.

## <a name="syntax"></a>Syntaxe

```
class CArchive
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Crée un objet `CArchive`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CArchive:: Abort](#abort)|Ferme une archive sans lever d’exception.|
|[CArchive::Close](#close)|Vide les `CFile`données non écrites et se déconnecte de.|
|[CArchive:: Flush](#flush)|Vide les données non écrites du tampon d’archive.|
|[CArchive:: GetFile](#getfile)|Obtient le `CFile` pointeur d’objet pour cette archive.|
|[CArchive:: GetObjectSchema](#getobjectschema)|Appelé à partir `Serialize` de la fonction pour déterminer la version de l’objet qui est désérialisé.|
|[CArchive:: IsBufferEmpty](#isbufferempty)|Détermine si la mémoire tampon a été vidée pendant un processus de réception Windows Sockets.|
|[CArchive:: IsLoading](#isloading)|Détermine si l’archive est en cours de chargement.|
|[CArchive::IsStoring](#isstoring)|Détermine si l’archive est stockée.|
|[CArchive::MapObject](#mapobject)|Place dans le mappage des objets qui ne sont pas sérialisés dans le fichier, mais qui sont disponibles pour les sous-objets à référencer.|
|[CArchive::Read](#read)|Lit les octets bruts.|
|[CArchive::ReadClass](#readclass)|Lit une référence de classe précédemment stockée avec `WriteClass`.|
|[CArchive::ReadObject](#readobject)|Appelle la `Serialize` fonction d’un objet pour le chargement.|
|[CArchive::ReadString](#readstring)|Lit une seule ligne de texte.|
|[CArchive:: SerializeClass](#serializeclass)|Lit ou écrit la référence de classe à `CArchive` l’objet en fonction de la direction `CArchive`de.|
|[CArchive::SetLoadParams](#setloadparams)|Définit la taille que le tableau de charge augmente. Doit être appelé avant le chargement d’un objet ou `MapObject` avant `ReadObject` ou l’appel à.|
|[CArchive::SetObjectSchema](#setobjectschema)|Définit le schéma d’objet stocké dans l’objet archive.|
|[CArchive::SetStoreParams](#setstoreparams)|Définit la taille de la table de hachage et la taille de bloc de la carte utilisée pour identifier les objets uniques pendant le processus de sérialisation.|
|[CArchive::Write](#write)|Écrit des octets bruts.|
|[CArchive:: WriteClass](#writeclass)|Écrit une référence au `CRuntimeClass`. `CArchive`|
|[CArchive::WriteObject](#writeobject)|Appelle la `Serialize` fonction d’un objet pour le stockage.|
|[CArchive::WriteString](#writestring)|Écrit une seule ligne de texte.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CArchive:: Operator&lt;&lt;](#operator_lt_lt)|Stocke les objets et les types primitifs dans l’archive.|
|[CArchive:: Operator&gt;&gt;](#operator_gt_gt)|Charge les objets et les types primitifs à partir de l’archive.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Notes

`CArchive`n’a pas de classe de base.

Par la suite, vous pouvez charger les objets à partir du stockage persistant, les reconstituer en mémoire. Ce processus qui consiste à rendre les données persistantes est appelé «sérialisation».

Vous pouvez considérer un objet archive comme un type de flux binaire. À l’instar d’un flux d’entrée/sortie, une archive est associée à un fichier et permet la mise en mémoire tampon de l’écriture et de la lecture des données vers et depuis le stockage. Un flux d’entrée/sortie traite les séquences de caractères ASCII, mais une archive traite les données d’objets binaires dans un format efficace et non redondant.

Vous devez créer un objet [CFile](../../mfc/reference/cfile-class.md) avant de pouvoir créer un `CArchive` objet. En outre, vous devez vous assurer que l’état de chargement/stockage de l’archive est compatible avec le mode d’ouverture du fichier. Vous êtes limité à une archive active par fichier.

Quand vous construisez `CArchive` un objet, vous l’attachez à un objet `CFile` de classe (ou une classe dérivée) qui représente un fichier ouvert. Vous spécifiez également si l’archive sera utilisée pour le chargement ou le stockage. Un `CArchive` objet peut traiter non seulement des types primitifs, mais également des objets de classes dérivées de [CObject](../../mfc/reference/cobject-class.md)conçues pour la sérialisation. Une classe sérialisable `Serialize` a généralement une fonction membre, et elle utilise généralement les macros [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) , comme décrit dans la classe `CObject`.

Les opérateurs d’extraction ( **>>** ) et d’insertion ( **<<** ) surchargés sont des interfaces de programmation d’archive pratiques qui prennent en charge à la fois les types primitifs et `CObject`les classes dérivées de.

`CArchive`prend également en charge la programmation avec les classes MFC Windows Sockets [CSocket](../../mfc/reference/csocket-class.md) et [CSocketFile](../../mfc/reference/csocketfile-class.md). La fonction membre [IsBufferEmpty](#isbufferempty) prend en charge cette utilisation.

Pour plus d’informations `CArchive`sur, consultez les articles [sérialisation](../../mfc/serialization-in-mfc.md) et [Windows Sockets: Utilisation de sockets avec](../../mfc/windows-sockets-using-sockets-with-archives.md)des archives.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CArchive`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="abort"></a>  CArchive::Abort

Appelez cette fonction pour fermer l’archive sans lever d’exception.

```
void Abort ();
```

### <a name="remarks"></a>Notes

Le `CArchive` destructeur appelle `Close`normalement, ce qui entraîne le vidage des données qui n’ont pas été enregistrées dans l' `CFile` objet associé. Cela peut entraîner des exceptions.

Lors de l’interception de ces exceptions, il est judicieux d' `Abort`utiliser, afin que la destruction `CArchive` de l’objet n’entraîne pas d’exceptions supplémentaires. Lors de la gestion `CArchive::Abort` des exceptions, ne lève pas d’exception en cas d’échec, car, `Abort` contrairement à [CArchive:: Close](#close), ignore les échecs.

Si vous avez utilisé **New** pour allouer l' `CArchive` objet sur le tas, vous devez le supprimer après avoir fermé le fichier.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CArchive:: WriteClass](#writeclass).

##  <a name="carchive"></a>  CArchive::CArchive

Construit un `CArchive` objet et spécifie s’il doit être utilisé pour charger ou stocker des objets.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Paramètres

*pFile*<br/>
Pointeur vers l' `CFile` objet qui est la source ou la destination ultime des données persistantes.

*nMode*<br/>
Indicateur qui spécifie si les objets sont chargés ou stockés dans l’archive. Le paramètre *nMode* doit avoir l’une des valeurs suivantes:

- `CArchive::load`Charge des données à partir de l’archive. Nécessite uniquement `CFile` une autorisation de lecture.

- `CArchive::store`Enregistre les données dans l’archive. Requiert `CFile` l’autorisation Write.

- `CArchive::bNoFlushOnDelete`Empêche l’archive d’appeler `Flush` automatiquement lorsque le destructeur d’archive est appelé. Si vous définissez cet indicateur, vous êtes chargé d’appeler `Close` explicitement avant l’appel du destructeur. Si vous ne le faites pas, vos données seront endommagées.

*nBufSize*<br/>
Entier qui spécifie la taille de la mémoire tampon de fichier interne, en octets. Notez que la taille de la mémoire tampon par défaut est de 4 096 octets. Si vous archivez régulièrement des objets volumineux, vous améliorerez les performances si vous utilisez une plus grande taille de mémoire tampon qui est un multiple de la taille de la mémoire tampon du fichier.

*lpBuf*<br/>
Pointeur facultatif vers une mémoire tampon de taille *nBufSize*fournie par l’utilisateur. Si vous ne spécifiez pas ce paramètre, l’archive alloue une mémoire tampon à partir du tas local et la libère lorsque l’objet est détruit. L’archive ne libère pas de mémoire tampon fournie par l’utilisateur.

### <a name="remarks"></a>Notes

Vous ne pouvez pas modifier cette spécification après avoir créé l’archive.

Vous ne pouvez pas `CFile` utiliser les opérations pour modifier l’état du fichier tant que vous n’avez pas fermé l’archive. Toute opération de ce type risque d’endommager l’intégrité de l’archive. Vous pouvez accéder à la position du pointeur de fichier à tout moment pendant la sérialisation en obtenant l’objet fichier de l’archive à partir de la fonction membre [GetFile](#getfile) , puis en utilisant la fonction [CFile:: GetPosition](../../mfc/reference/cfile-class.md#getposition) . Vous devez appeler [CArchive:: Flush](#flush) avant d’obtenir la position du pointeur de fichier.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>  CArchive::Close

Vide les données restantes dans la mémoire tampon, ferme l’archive et déconnecte l’archive du fichier.

```
void Close();
```

### <a name="remarks"></a>Notes

Aucune autre opération sur l’archive n’est autorisée. Après avoir fermé une archive, vous pouvez créer une autre Archive pour le même fichier, ou vous pouvez fermer le fichier.

La fonction `Close` membre garantit que toutes les données sont transférées de l’archive vers le fichier et rend l’archive indisponible. Pour terminer le transfert du fichier vers le support de stockage, vous devez d’abord utiliser [CFile:: Close](../../mfc/reference/cfile-class.md#close) , puis détruire `CFile` l’objet.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CArchive:: WriteString](#writestring).

##  <a name="flush"></a>  CArchive::Flush

Force l’écriture dans le fichier des données restantes dans le tampon d’archivage.

```
void Flush();
```

### <a name="remarks"></a>Notes

La fonction `Flush` membre garantit que toutes les données sont transférées de l’archive vers le fichier. Vous devez appeler [CFile:: Close](../../mfc/reference/cfile-class.md#close) pour terminer le transfert du fichier vers le support de stockage.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>  CArchive::GetFile

Obtient le `CFile` pointeur d’objet pour cette archive.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur constant vers l' `CFile` objet en cours d’utilisation.

### <a name="remarks"></a>Notes

Vous devez vider l’archive avant d' `GetFile`utiliser.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>  CArchive::GetObjectSchema

Appelez cette fonction à partir `Serialize` de la fonction pour déterminer la version de l’objet qui est en cours de désérialisation.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Valeur de retour

Pendant la désérialisation, version de l’objet en cours de lecture.

### <a name="remarks"></a>Notes

L’appel de cette fonction est valide uniquement `CArchive` lorsque l’objet est chargé ( [CArchive:: IsLoading](#isloading) retourne une valeur différente de zéro). Il doit s’agir du premier appel dans `Serialize` la fonction et appelé une seule fois. Une valeur de retour (UINT)-1 indique que le numéro de version est inconnu.

Une `CObject`classe dérivée de VERSIONABLE_SCHEMA peut utiliser des combinés (à l’aide de **l’opérateur or**au niveau du bit) avec la version de schéma proprement dite (dans la macro IMPLEMENT_SERIAL) pour `Serialize` créer un «objet avec version», c’est-à-dire un objet dont la fonction membre peut lire plusieurs versions. La fonctionnalité d’infrastructure par défaut (sans VERSIONABLE_SCHEMA) consiste à lever une exception lorsque la version ne correspond pas.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>  CArchive::IsBufferEmpty

Appelez cette fonction membre pour déterminer si la mémoire tampon interne de l’objet archive est vide.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la mémoire tampon de l’archive est vide; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est fournie pour prendre en charge la programmation avec la classe `CSocketFile`Windows Sockets MFC. Vous n’avez pas besoin de l’utiliser pour une archive associée à `CFile` un objet.

La raison de l' `IsBufferEmpty` utilisation de avec une archive associée `CSocketFile` à un objet est que la mémoire tampon de l’archive peut contenir plusieurs messages ou enregistrements. Après avoir reçu un message, vous devez `IsBufferEmpty` utiliser pour contrôler une boucle qui continue à recevoir des données jusqu’à ce que la mémoire tampon soit vide. Pour plus d’informations, consultez la fonction membre [Receive](../../mfc/reference/casyncsocket-class.md#receive) de `CAsyncSocket`la classe, qui montre comment `IsBufferEmpty`utiliser.

Pour plus d’informations, [consultez Windows Sockets: Utilisation de sockets avec](../../mfc/windows-sockets-using-sockets-with-archives.md)des archives.

##  <a name="isloading"></a>CArchive:: IsLoading

Détermine si l’archive charge des données.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’archive est actuellement utilisée pour le chargement; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par les `Serialize` fonctions des classes archivées.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>  CArchive::IsStoring

Détermine si l’archive stocke des données.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’archive est actuellement utilisée pour le stockage; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par les `Serialize` fonctions des classes archivées.

Si l' `IsStoring` état d’une archive est différent de zéro, son `IsLoading` État est 0, et vice versa.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>  CArchive::MapObject

Appelez cette fonction membre pour placer dans le mappage des objets qui ne sont pas véritablement sérialisés dans le fichier, mais qui sont disponibles pour les sous-objets à référencer.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*pOb*<br/>
Pointeur constant vers l’objet stocké.

### <a name="remarks"></a>Notes

Par exemple, vous pouvez ne pas sérialiser un document, mais vous sérialisez les éléments qui font partie du document. En appelant `MapObject`, vous autorisez ces éléments, ou sous-objets, à référencer le document. En outre, les sous-éléments sérialisés peuvent sérialiser leur pointeur arrière *m_pDocument* .

Vous pouvez appeler `MapObject` lorsque vous stockez et chargez à `CArchive` partir de l’objet. `MapObject`Ajoute l’objet spécifié aux structures de données internes gérées par `CArchive` l’objet pendant la sérialisation et la désérialisation, mais contrairement à [ReadObject](#readobject) et [writeObject](#writeobject), il n’appelle pas Serialize sur l’objet.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>  CArchive::m_pDocument

Défini sur la valeur NULL par défaut, ce pointeur `CDocument` vers un peut être défini sur n’importe quel `CArchive` utilisateur de l’instance.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Notes

Ce pointeur est couramment utilisé pour transmettre des informations supplémentaires sur le processus de sérialisation à tous les objets en cours de sérialisation. Pour ce faire, vous devez initialiser le pointeur avec le document `CDocument`(une classe dérivée) qui est sérialisée, de telle sorte que les objets dans le document puissent accéder au document si nécessaire. Ce pointeur est également utilisé par `COleClientItem` les objets pendant la sérialisation.

L’infrastructure définit *m_pDocument* sur le document qui est sérialisé lorsqu’un utilisateur émet une commande fichier ouvrir ou enregistrer. Si vous sérialisez un document de conteneur de liaison et d’incorporation d’objets (OLE) pour des raisons autres que l’ouverture ou l’enregistrement de fichiers, vous devez définir explicitement *m_pDocument*. Par exemple, vous pouvez effectuer cette opération lors de la sérialisation d’un document conteneur dans le presse-papiers.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>CArchive:: Operator&lt;&lt;

Stocke l’objet ou le type primitif indiqué dans l’archive.

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>Valeur de retour

`CArchive` Référence qui active plusieurs opérateurs d’insertion sur une seule ligne.

### <a name="remarks"></a>Notes

Les deux dernières versions ci-dessus sont spécifiquement destinées au stockage des entiers 64 bits.

Si vous avez utilisé la macro IMPLEMENT_SERIAL dans votre implémentation de classe, l’opérateur d’insertion surchargé pour `CObject` appelle le protégé `WriteObject`. Cette fonction appelle à son tour la `Serialize` fonction de la classe.

L’opérateur d’insertion [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (< <) prend en charge le vidage et le stockage des diagnostics dans une archive.

### <a name="example"></a>Exemples

Cet exemple illustre l’utilisation de l' `CArchive` opérateur d’insertion < < avec les types **int** et **long** .

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Exemples

Cet exemple 2 montre l’utilisation de l' `CArchive` opérateur d’insertion < < avec `CStringT` le type.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>CArchive:: Operator&gt;&gt;

Charge l’objet ou le type primitif indiqué à partir de l’archive.

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>Valeur de retour

`CArchive` Référence qui active plusieurs opérateurs d’extraction sur une seule ligne.

### <a name="remarks"></a>Notes

Les deux dernières versions ci-dessus concernent spécifiquement le chargement d’entiers 64 bits.

Si vous avez utilisé la macro IMPLEMENT_SERIAL dans votre implémentation de classe, les opérateurs d’extraction surchargés pour `CObject` appeler la fonction protégée `ReadObject` (avec un pointeur de classe à l’exécution autre que zéro). Cette fonction appelle à son tour la `Serialize` fonction de la classe.

L’opérateur d’extraction [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (> >) prend en charge le chargement à partir d’une archive.

### <a name="example"></a>Exemple

Cet exemple illustre l’utilisation de l' `CArchive` opérateur d’extraction > > avec le type **int** .

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Exemple

Cet exemple illustre l’utilisation des `CArchive` opérateurs d’insertion et d’extraction <\< et > > avec `CStringT` le type.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>  CArchive::Read

Lit un nombre spécifié d’octets à partir de l’archive.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur vers une mémoire tampon fournie par l’utilisateur qui doit recevoir les données lues à partir de l’archive.

*nMax*<br/>
Entier non signé spécifiant le nombre d’octets à lire à partir de l’archive.

### <a name="return-value"></a>Valeur de retour

Entier non signé contenant le nombre d’octets réellement lus. Si la valeur de retour est inférieure au nombre demandé, la fin du fichier a été atteinte. Aucune exception n’est levée dans la condition de fin de fichier.

### <a name="remarks"></a>Notes

L’archive n’interprète pas les octets.

Vous pouvez utiliser la `Read` fonction membre dans votre `Serialize` fonction pour lire les structures ordinaires contenues dans vos objets.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>  CArchive::ReadClass

Appelez cette fonction membre pour lire une référence à une classe précédemment stockée avec [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Paramètres

*pClassRefRequested*<br/>
Pointeur vers la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui correspond à la référence de classe demandée. Peut avoir la valeur NULL.

*pSchema*<br/>
Pointeur vers un schéma de la classe d’exécution précédemment stockée.

*pObTag*<br/>
Nombre qui fait référence à la balise unique d’un objet. Utilisé en interne par l’implémentation de [ReadObject](#readobject). Exposé pour la programmation avancée uniquement; *pObTag* doit normalement avoir la valeur null.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) .

### <a name="remarks"></a>Notes

Si *pClassRefRequested* n’a pas la `ReadClass` valeur null, vérifie que les informations de classe archivées sont compatibles avec votre classe d’exécution. S’il n’est pas compatible `ReadClass` , lèvera un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Votre classe d’exécution doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); Sinon, `ReadClass` lèvera un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Si *pSchema* a la valeur null, le schéma de la classe stockée peut être récupéré en appelant [CArchive:: GetObjectSchema](#getobjectschema); Sinon, <strong>\*</strong> *pSchema* contiendra le schéma de la classe d’exécution précédemment stockée.

Vous pouvez utiliser [SerializeClass](#serializeclass) au lieu `ReadClass`de, qui gère la lecture et l’écriture de la référence de classe.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CArchive:: WriteClass](#writeclass).

##  <a name="readobject"></a>  CArchive::ReadObject

Lit les données d’objet à partir de l’archive et construit un objet du type approprié.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Paramètres

*pClass*<br/>
Pointeur constant vers la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui correspond à l’objet que vous souhaitez lire.

### <a name="return-value"></a>Valeur de retour

Pointeur [CObject](../../mfc/reference/cobject-class.md) qui doit être casté en toute sécurité vers la classe dérivée correcte à l’aide de [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Notes

Cette fonction est normalement appelée par l' `CArchive` opérateur d' **>>** extraction () surchargé pour un pointeur [CObject](../../mfc/reference/cobject-class.md) . `ReadObject`, à son tour, appelle `Serialize` la fonction de la classe archivée.

Si vous fournissez un paramètre *pclass* différent de zéro, qui est obtenu par la macro [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , la fonction vérifie la classe Runtime de l’objet archivé. Cela suppose que vous avez utilisé la macro IMPLEMENT_SERIAL dans l’implémentation de la classe.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CArchive:: WriteObject](#writeobject).

##  <a name="readstring"></a>  CArchive::ReadString

Appelez cette fonction membre pour lire les données de texte dans une mémoire tampon à partir du `CArchive` fichier associé à l’objet.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Paramètres

*rString*<br/>
Référence à une [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contiendra la chaîne résultante après sa lecture à partir du fichier associé à l’objet CArchive.

*lpsz*<br/>
Spécifie un pointeur vers une mémoire tampon fournie par l’utilisateur qui recevra une chaîne de texte se terminant par un caractère null.

*nMax*<br/>
Spécifie le nombre maximal de caractères à lire. Doit être inférieur à la taille de la mémoire tampon *lpsz* .

### <a name="return-value"></a>Valeur de retour

Dans la version qui retourne BOOL, TRUE en cas de réussite; FALSe dans le cas contraire.

Dans la version qui retourne un `LPTSTR`, pointeur vers la mémoire tampon contenant les données textuelles; NULL si la fin du fichier a été atteinte.

### <a name="remarks"></a>Notes

Dans la version de la fonction membre avec le paramètre *nmax* , la mémoire tampon contient une limite de *nmax* -1 caractères. La lecture est arrêtée par une paire retour chariot-saut de ligne. Les caractères de saut de ligne de fin sont toujours supprimés. Un caractère null (' \ 0 ') est ajouté dans les deux cas.

[CArchive:: Read](#read) est également disponible pour l’entrée en mode texte, mais elle ne se termine pas sur une paire retour chariot-saut de ligne.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CArchive:: WriteString](#writestring).

##  <a name="serializeclass"></a>  CArchive::SerializeClass

Appelez cette fonction membre lorsque vous souhaitez stocker et charger les informations de version d’une classe de base.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Paramètres

*pClassRef*<br/>
Pointeur vers un objet de classe au moment de l’exécution pour la classe de base.

### <a name="remarks"></a>Notes

`SerializeClass`lit ou écrit la référence à une classe dans l' `CArchive` objet, en fonction de la direction `CArchive`de. Utilisez `SerializeClass` à la place de [ReadClass](#readclass) et [WriteClass](#writeclass) pour sérialiser facilement des objets de classe de base. `SerializeClass` nécessite moins de code et moins de paramètres.

Comme `ReadClass` ,`SerializeClass` vérifie que les informations de classe archivées sont compatibles avec votre classe d’exécution. S’il n’est pas compatible `SerializeClass` , lèvera un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Votre classe d’exécution doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); Sinon, `SerializeClass` lèvera un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Utilisez la macro [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) pour récupérer la valeur du paramètre *pRuntimeClass* . La classe de base doit avoir utilisé la macro [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>  CArchive::SetLoadParams

Appelez `SetLoadParams` lorsque vous allez lire un grand nombre d' `CObject`objets dérivés de à partir d’une archive.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Paramètres

*nGrowBy*<br/>
Nombre minimal d’emplacements d’éléments à allouer si une augmentation de la taille est nécessaire.

### <a name="remarks"></a>Notes

`CArchive`utilise un tableau de charge pour résoudre les références aux objets stockés dans l’archive. `SetLoadParams`vous permet de définir la taille que le tableau de charge augmente.

Vous ne devez pas `SetLoadParams` appeler après le chargement d’un objet, ou après l’appel de [MapObject](#mapobject) ou [ReadObject](#readobject) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>  CArchive::SetObjectSchema

Appelez cette fonction membre pour définir le schéma d’objet stocké dans l’objet archive sur *nSchema*.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Paramètres

*nSchema*<br/>
Spécifie le schéma de l’objet.

### <a name="remarks"></a>Notes

L’appel suivant à [GetObjectSchema](#getobjectschema) renverra la valeur stockée dans *nSchema*.

À `SetObjectSchema` utiliser pour le contrôle de version avancé; par exemple, lorsque vous souhaitez forcer une version particulière à être lue `Serialize` dans une fonction d’une classe dérivée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>  CArchive::SetStoreParams

À `SetStoreParams` utiliser lors du stockage d’un `CObject`grand nombre d’objets dérivés de dans une archive.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Paramètres

*nHashSize*<br/>
Taille de la table de hachage pour les mappages de pointeur d’interface. Doit être un nombre premier.

*nBlockSize*<br/>
Spécifie la granularité d’allocation de mémoire pour l’extension des paramètres. Doit être une puissance de 2 pour des performances optimales.

### <a name="remarks"></a>Notes

`SetStoreParams`vous permet de définir la taille de la table de hachage et la taille de bloc de la carte utilisée pour identifier les objets uniques pendant le processus de sérialisation.

Vous ne devez pas `SetStoreParams` appeler une fois les objets stockés ou après l’appel de [MapObject](#mapobject) ou [writeObject](#writeobject) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>  CArchive::Write

Écrit un nombre spécifié d’octets dans l’archive.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur vers une mémoire tampon fournie par l’utilisateur qui contient les données à écrire dans l’archive.

*nMax*<br/>
Entier qui spécifie le nombre d’octets à écrire dans l’archive.

### <a name="remarks"></a>Notes

L’archive ne formate pas les octets.

Vous pouvez utiliser la `Write` fonction membre dans votre `Serialize` fonction pour écrire des structures ordinaires contenues dans vos objets.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>  CArchive::WriteClass

Utilisez `WriteClass` pour stocker la version et les informations de classe d’une classe de base lors de la sérialisation de la classe dérivée.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Paramètres

*pClassRef*<br/>
Pointeur vers la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui correspond à la référence de classe demandée.

### <a name="remarks"></a>Notes

`WriteClass`écrit une référence à [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pour la classe de base dans le `CArchive`. Utilisez [CArchive:: ReadClass](#readclass) pour récupérer la référence.

`WriteClass`vérifie que les informations de classe archivées sont compatibles avec votre classe d’exécution. S’il n’est pas compatible `WriteClass` , lèvera un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Votre classe d’exécution doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); Sinon, `WriteClass` lèvera un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Vous pouvez utiliser [SerializeClass](#serializeclass) au lieu `WriteClass`de, qui gère la lecture et l’écriture de la référence de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>  CArchive::WriteObject

Stocke le `CObject` spécifié dans l’archive.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*pOb*<br/>
Pointeur constant vers l’objet stocké.

### <a name="remarks"></a>Notes

Cette fonction est normalement appelée par l' `CArchive` opérateur d' **<<** insertion () surchargé pour `CObject`. `WriteObject`, à son tour, appelle `Serialize` la fonction de la classe archivée.

Vous devez utiliser la macro IMPLEMENT_SERIAL pour activer l’archivage. `WriteObject`écrit le nom de la classe ASCII dans l’archive. Ce nom de classe est validé ultérieurement au cours du processus de chargement. Un schéma d’encodage spécial empêche la duplication inutile du nom de classe pour plusieurs objets de la classe. Ce schéma empêche également le stockage redondant d’objets qui sont des cibles de plus d’un pointeur.

La méthode d’encodage d’objet exacte (y compris la présence du nom de classe ASCII) est un détail d’implémentation et peut changer dans les futures versions de la bibliothèque.

> [!NOTE]
>  Terminez la création, la suppression et la mise à jour de tous vos objets avant de commencer à les archiver. Votre archive sera endommagée si vous combinez l’archivage avec la modification de l’objet.

### <a name="example"></a>Exemples

Pour obtenir une définition de la `CAge`classe, consultez l’exemple pour [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>  CArchive::WriteString

Utilisez cette fonction membre pour écrire des données à partir d’une mémoire tampon dans le `CArchive` fichier associé à l’objet.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
Spécifie un pointeur vers une mémoire tampon contenant une chaîne de texte se terminant par null.

### <a name="remarks"></a>Notes

Le caractère null de fin (' \ 0 ') n’est pas écrit dans le fichier; il ne s’agit pas non plus d’un saut de ligne automatiquement écrit.

`WriteString`lève une exception en réponse à plusieurs conditions, y compris la condition Disk-Full.

`Write`est également disponible, mais au lieu de se terminer par un caractère null, il écrit le nombre d’octets demandé dans le fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[CSocket, classe](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
