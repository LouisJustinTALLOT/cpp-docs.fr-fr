---
title: CArchive, classe
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
ms.openlocfilehash: ef8b6ec9060e8c15dd45f8203dadd2a2aca9e168
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753123"
---
# <a name="carchive-class"></a>CArchive, classe

Vous permet d’enregistrer un réseau complexe d’objets sous une forme binaire permanente (généralement le stockage de disque) qui persiste après la suppression de ces objets.

## <a name="syntax"></a>Syntaxe

```
class CArchive
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Crée un objet `CArchive` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CArchive::Abort](#abort)|Ferme une archive sans jeter d’exception.|
|[CArchive::Fermer](#close)|Flushes données non écrites `CFile`et se déconnecte de la .|
|[CArchive::Flush](#flush)|Rincer les données non écrites du tampon d’archive.|
|[CArchive::GetFile](#getfile)|Obtient `CFile` le pointeur d’objet pour cette archive.|
|[CArchive::GetObjectSchema](#getobjectschema)|Appelé à `Serialize` partir de la fonction pour déterminer la version de l’objet qui est déséialisé.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Détermine si le tampon a été vidé au cours d’un processus de réception de windows Sockets.|
|[CArchive::IsLoading](#isloading)|Détermine si l’archive est en charge.|
|[CArchive::IsStoring](#isstoring)|Détermine si l’archive est entreposée.|
|[CArchive::MapObject](#mapobject)|Place des objets dans la carte qui ne sont pas sérialisés dans le fichier, mais qui sont disponibles pour les sous-exemples à référence.|
|[CArchive::Lire](#read)|Lit les octets crus.|
|[CArchive::Lire La classe](#readclass)|Lit une référence de `WriteClass`classe précédemment stockée avec .|
|[CArchive::LireObject](#readobject)|Appelle la fonction `Serialize` d’un objet pour le chargement.|
|[CArchive::ReadString](#readstring)|Lit une seule ligne de texte.|
|[CArchive::SerializeClass](#serializeclass)|Lit ou écrit la `CArchive` référence de classe à `CArchive`l’objet en fonction de la direction de la .|
|[CArchive::SetLoadParams](#setloadparams)|Définit la taille à laquelle le tableau de charge se développe. Doit être appelé avant que `MapObject` tout `ReadObject` objet soit chargé ou avant ou est appelé.|
|[CArchive::SetObjectSchema](#setobjectschema)|Définit le schéma d’objet stocké dans l’objet d’archives.|
|[CArchive::SetStoreParams](#setstoreparams)|Définit la taille de la table de hachage et la taille du bloc de la carte utilisée pour identifier les objets uniques pendant le processus de sérialisation.|
|[CArchive::Écrire](#write)|Écrit des octets crus.|
|[CArchive::WriteClass](#writeclass)|Écrit une référence `CRuntimeClass` à `CArchive`la .|
|[CArchive::WriteObject](#writeobject)|Appelle la `Serialize` fonction d’un objet pour le stockage.|
|[CArchive::WriteString](#writestring)|Écrit une seule ligne de texte.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CArchive::opérateur&lt;&lt;](#operator_lt_lt)|Stocke des objets et des types primitifs à l’archive.|
|[CArchive::opérateur&gt;&gt;](#operator_gt_gt)|Charge les objets et les types primitifs de l’archive.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Notes

`CArchive`n’a pas de classe de base.

Plus tard, vous pouvez charger les objets à partir d’un stockage persistant, les reconstituer dans la mémoire. Ce processus de persistance des données s’appelle la « sérialisation ».

Vous pouvez penser à un objet d’archives comme une sorte de flux binaire. Comme un flux d’entrée/sortie, une archive est associée à un fichier et permet la rédaction et la lecture tamponnées des données à l’adresse et à partir du stockage. Un flux d’entrée/sortie traite les séquences des caractères ASCII, mais une archive traite les données d’objets binaires dans un format efficace et nonredundant.

Vous devez créer un objet [CFile](../../mfc/reference/cfile-class.md) avant de pouvoir créer un `CArchive` objet. De plus, vous devez vous assurer que l’état de charge/magasin de l’archive est compatible avec le mode ouvert du fichier. Vous êtes limité à une archive active par fichier.

Lorsque vous `CArchive` construisez un objet, vous `CFile` l’attachez à un objet de classe (ou à une classe dérivée) qui représente un fichier ouvert. Vous spécifiez également si l’archive sera utilisée pour le chargement ou le stockage. Un `CArchive` objet peut traiter non seulement les types primitifs, mais aussi les objets de classes dérivées de [CObject](../../mfc/reference/cobject-class.md)conçues pour la sérialisation. Une classe sérialisable `Serialize` a généralement une fonction de membre, et il utilise habituellement `CObject`les macros [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL,](../../mfc/reference/run-time-object-model-services.md#implement_serial) comme décrit sous la classe .

L’extraction surchargée **>>**( ) **<<** et l’insertion ( ) les opérateurs `CObject`sont des interfaces de programmation d’archives pratiques qui prennent en charge à la fois les types primitifs et les classes dérivées.

`CArchive`prend également en charge la programmation avec les classes MFC Windows Sockets [CSocket](../../mfc/reference/csocket-class.md) et [CSocketFile](../../mfc/reference/csocketfile-class.md). La fonction membre [IsBufferEmpty](#isbufferempty) prend en charge cette utilisation.

Pour plus `CArchive`d’informations sur , voir les articles [Serialization](../../mfc/serialization-in-mfc.md) et [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CArchive`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="carchiveabort"></a><a name="abort"></a>CArchive::Abort

Appelez cette fonction pour fermer les archives sans jeter une exception.

```cpp
void Abort ();
```

### <a name="remarks"></a>Notes

Le `CArchive` destructeur appellera `Close`normalement , qui chassera toutes les données `CFile` qui n’ont pas été enregistrées sur l’objet associé. Cela peut entraîner des exceptions.

Lors de la capture de ces `Abort`exceptions, il est `CArchive` une bonne idée d’utiliser , de sorte que la destruction de l’objet ne provoque pas d’autres exceptions. Lors de `CArchive::Abort` la manipulation des exceptions, ne jette pas une exception `Abort` sur les échecs parce que, contrairement à [CArchive::Close](#close), ignore les échecs.

Si vous **new** avez utilisé `CArchive` nouveau pour allouer l’objet sur le tas, alors vous devez le supprimer après la fermeture du fichier.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CArchive:WriteClass](#writeclass).

## <a name="carchivecarchive"></a><a name="carchive"></a>CArchive::CArchive

Construit un `CArchive` objet et précise s’il sera utilisé pour le chargement ou le stockage d’objets.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Paramètres

*pFile (en)*<br/>
Un pointeur `CFile` vers l’objet qui est la source ou la destination ultime des données persistantes.

*nMode*<br/>
Un drapeau qui précise si les objets seront chargés ou stockés à l’archive. Le *paramètre nMode* doit avoir l’une des valeurs suivantes :

- `CArchive::load`Charge les données de l’archive. Nécessite `CFile` seulement la permission de lecture.

- `CArchive::store`Enregistre les données de l’archive. Nécessite `CFile` une autorisation d’écriture.

- `CArchive::bNoFlushOnDelete`Empêche l’archive d’appeler `Flush` automatiquement lorsque le destructeur d’archives est appelé. Si vous définissez ce drapeau, `Close` vous êtes responsable d’appeler explicitement avant que le destructeur soit appelé. Si vous ne le faites pas, vos données seront corrompues.

*nBufSize*<br/>
Un intégrant qui spécifie la taille du tampon de fichier interne, dans les octets. Notez que la taille du tampon par défaut est de 4 096 octets. Si vous archivez régulièrement de gros objets, vous améliorerez les performances si vous utilisez une plus grande taille de tampon qui est un multiple de la taille du tampon de fichier.

*lpBuf*<br/>
Un pointeur optionnel à un tampon fourni par l’utilisateur de taille *nBufSize*. Si vous ne spécifiez pas ce paramètre, l’archive alloue un tampon du tas local et le libère lorsque l’objet est détruit. L’archive ne libère pas un tampon fourni par l’utilisateur.

### <a name="remarks"></a>Notes

Vous ne pouvez pas modifier cette spécification après avoir créé l’archive.

Vous ne `CFile` pouvez pas utiliser les opérations pour modifier l’état du fichier tant que vous n’avez pas fermé l’archive. Une telle opération portera atteinte à l’intégrité des archives. Vous pouvez accéder à la position du pointeur de fichier à tout moment pendant la sérialisation en obtenant l’objet de fichier de l’archive à partir de la fonction membre [GetFile,](#getfile) puis en utilisant la fonction [CFile::GetPosition.](../../mfc/reference/cfile-class.md#getposition) Vous devez appeler [CArchive::Flush](#flush) avant d’obtenir la position du pointeur de fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>CArchive::Fermer

Rincer toutes les données restantes dans le tampon, ferme l’archive et déconnecte l’archive du fichier.

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Aucune autre opération sur l’archive n’est autorisée. Après avoir fermé une archive, vous pouvez créer une autre archive pour le même fichier ou vous pouvez fermer le fichier.

La fonction `Close` membre garantit que toutes les données sont transférées de l’archive au fichier, et qu’elles rendent l’archive indisponible. Pour effectuer le transfert du fichier vers le support de stockage, vous devez `CFile` d’abord utiliser [CFile : : Fermer](../../mfc/reference/cfile-class.md#close) puis détruire l’objet.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CArchive:WriteString](#writestring).

## <a name="carchiveflush"></a><a name="flush"></a>CArchive::Flush

Force toute donnée restante dans le tampon d’archivage à être écrite au fichier.

```cpp
void Flush();
```

### <a name="remarks"></a>Notes

La fonction `Flush` membre garantit que toutes les données sont transférées de l’archive au fichier. Vous devez appeler [CFile: :Fermer](../../mfc/reference/cfile-class.md#close) pour terminer le transfert du fichier au support de stockage.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>CArchive::GetFile

Obtient `CFile` le pointeur d’objet pour cette archive.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CFile` constant de l’objet utilisé.

### <a name="remarks"></a>Notes

Vous devez rincer `GetFile`l’archive avant d’utiliser .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive::GetObjectSchema

Appelez cette fonction `Serialize` de la fonction pour déterminer la version de l’objet qui est actuellement déséialisé.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Valeur de retour

Pendant la désétérialisation, la version de l’objet lu.

### <a name="remarks"></a>Notes

Appeler cette fonction n’est valable que lorsque l’objet `CArchive` est chargé ( [CArchive::IsLoading](#isloading) retourne nonzero). Il devrait être le `Serialize` premier appel dans la fonction et appelé qu’une seule fois. Une valeur de retour de (UINT)-1 indique que le numéro de version est inconnu.

Une `CObject`classe dérivée peut utiliser VERSIONABLE_SCHEMA combiné (à l’aide de bitwise **OU**) avec la version schéma elle-même (dans `Serialize` la IMPLEMENT_SERIAL macro) pour créer un «objet versionnable», c’est-à-dire un objet dont la fonction de membre peut lire plusieurs versions. La fonctionnalité de cadre par défaut (sans VERSIONABLE_SCHEMA) est de jeter une exception lorsque la version est dépareillée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive::IsBufferEmpty

Appelez cette fonction de membre pour déterminer si le tampon interne de l’objet d’archives est vide.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le tampon de l’archive est vide; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est fournie pour prendre en charge `CSocketFile`la programmation avec la classe MFC Windows Sockets . Vous n’avez pas besoin de l’utiliser pour une archive associée à un `CFile` objet.

La raison `IsBufferEmpty` de l’utilisation `CSocketFile` avec une archive associée à un objet est que le tampon de l’archive peut contenir plus d’un message ou un enregistrement. Après avoir reçu un `IsBufferEmpty` message, vous devez utiliser pour contrôler une boucle qui continue de recevoir des données jusqu’à ce que le tampon soit vide. Pour plus d’informations, consultez `CAsyncSocket`la fonction membre `IsBufferEmpty` [Receive](../../mfc/reference/casyncsocket-class.md#receive) de la classe , qui montre comment utiliser .

Pour plus d’informations, voir [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="carchiveisloading"></a><a name="isloading"></a>CArchive::IsLoading

Détermine si l’archive est le chargement des données.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’archive est actuellement utilisée pour le chargement; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction de membre `Serialize` est appelée par les fonctions des classes archivées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>CArchive::IsStoring

Détermine si l’archive stocke des données.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’archive est actuellement utilisée pour le stockage; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction de membre `Serialize` est appelée par les fonctions des classes archivées.

Si `IsStoring` l’état d’une archive n’est pas zéro, alors son `IsLoading` statut est de 0, et vice versa.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>CArchive::MapObject

Appelez cette fonction de membre pour placer des objets dans la carte qui ne sont pas vraiment sérialisés dans le fichier, mais qui sont disponibles pour les sous-exemples à référence.

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*Pob*<br/>
Un pointeur constant de l’objet stocké.

### <a name="remarks"></a>Notes

Par exemple, il se peut que vous ne sérialisiez pas un document, mais vous sérialisez les éléments qui font partie du document. En `MapObject`appelant , vous permettez à ces éléments, ou sous-indicateurs, de référencer le document. En outre, les subitems sérialisés peuvent sérialiser leur *m_pDocument* pointeur arrière.

Vous pouvez `MapObject` appeler lorsque vous stockez et chargez à partir de l’objet. `CArchive` `MapObject`ajoute l’objet spécifié aux structures de `CArchive` données internes maintenues par l’objet lors de la sérialisation et de la désélisement, mais contrairement à [ReadObject](#readobject) et [WriteObject](#writeobject), il n’appelle pas sérialiser sur l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>CArchive::m_pDocument

Défini à NULL par défaut, `CDocument` ce pointeur à un `CArchive` peut être réglé à tout ce que l’utilisateur de l’instance veut.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Notes

Une utilisation courante de ce pointeur est de transmettre des informations supplémentaires sur le processus de sérialisation à tous les objets en cours de sérialisation. Ceci est réalisé en initialisant le `CDocument`pointeur avec le document (une classe dérivée) qui est en cours de sérialisation, de telle sorte que les objets dans le document peuvent accéder au document si nécessaire. Ce pointeur est `COleClientItem` également utilisé par les objets lors de la sérialisation.

Le cadre définit *m_pDocument* au document en cours de sérialisation lorsqu’un utilisateur émet une commande d’ouverture de fichier ou d’enregistrement. Si vous sérialisez un document de conteneurs de liaison et d’intégration d’objets (OLE) pour des raisons autres que File Open ou Save, vous devez définir explicitement *m_pDocument*. Par exemple, vous le feriez lors de la sérialisation d’un document de conteneur au Clipboard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive::opérateur&lt;&lt;

Stocke l’objet indiqué ou le type primitif à l’archive.

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

Une `CArchive` référence qui permet à plusieurs opérateurs d’insertion sur une seule ligne.

### <a name="remarks"></a>Notes

Les deux dernières versions ci-dessus sont spécifiquement pour stocker des entiers 64 bits.

Si vous avez utilisé la macro IMPLEMENT_SERIAL dans votre mise en `CObject` œuvre `WriteObject`de classe, alors l’opérateur d’insertion surchargé pour les appels protégés . Cette fonction, à son `Serialize` tour, appelle la fonction de la classe.

[L’opérateur d’insertion CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (<<) prend en charge le dumping diagnostique et le stockage dans une archive.

### <a name="example"></a>Exemple

Cet exemple montre l’utilisation de l’opérateur `CArchive` d’insertion << avec les types **int** et **longs.**

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Exemple

Cet exemple 2 démontre l’utilisation de `CArchive` l’opérateur `CStringT` d’insertion << avec le type.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive::opérateur&gt;&gt;

Charge l’objet indiqué ou le type primitif de l’archive.

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

Une `CArchive` référence qui permet à plusieurs opérateurs d’extraction sur une seule ligne.

### <a name="remarks"></a>Notes

Les deux dernières versions ci-dessus sont spécifiquement pour le chargement des entiers 64 bits.

Si vous avez utilisé la macro IMPLEMENT_SERIAL dans votre mise en `CObject` œuvre `ReadObject` de classe, alors les opérateurs d’extraction surchargés pour appeler la fonction protégée (avec un pointeur de classe de temps d’exécution non zéro). Cette fonction, à son `Serialize` tour, appelle la fonction de la classe.

L’opérateur d’extraction [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (>>) prend en charge le chargement à partir d’une archive.

### <a name="example"></a>Exemple

Cet exemple montre l’utilisation de l’opérateur `CArchive` d’extraction >> avec le type **int.**

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Exemple

Cet exemple montre l’utilisation des opérateurs `CArchive` d’insertion et d’extraction <\< et >> avec le `CStringT` type.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>CArchive::Lire

Lit un nombre spécifié d’octets de l’archive.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Un pointeur vers un tampon fourni par l’utilisateur qui doit recevoir les données lues à partir de l’archive.

*Nmax*<br/>
Un insignable précisant le nombre d’octets à lire dans les archives.

### <a name="return-value"></a>Valeur de retour

Un integer non signé contenant le nombre d’octets effectivement lu. Si la valeur de déclaration est inférieure au nombre demandé, la fin du dossier a été atteinte. Aucune exception n’est accordée à l’état de fin de dossier.

### <a name="remarks"></a>Notes

L’archive n’interprète pas les octets.

Vous pouvez `Read` utiliser la `Serialize` fonction membre dans votre fonction pour lire les structures ordinaires qui sont contenues dans vos objets.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>CArchive::Lire La classe

Appelez cette fonction de membre pour lire une référence à une classe précédemment stockée avec [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Paramètres

*pClassRefRequested*<br/>
Un pointeur à la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui correspond à la référence de classe demandée. Sa valeur peut être NULL.

*pSchema*<br/>
Un pointeur à un schéma de la classe de temps d’exécution précédemment stocké.

*pObTag (en)*<br/>
Un nombre qui fait référence à l’étiquette unique d’un objet. Utilisé en interne par la mise en œuvre de [ReadObject](#readobject). Exposé pour une programmation avancée seulement; *pObTag* devrait normalement être NULL.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la structure [CRuntimeClass.](../../mfc/reference/cruntimeclass-structure.md)

### <a name="remarks"></a>Notes

Si *pClassRefRequested* n’est pas NULL, `ReadClass` vérifie que les informations de classe archivées sont compatibles avec votre classe de temps d’exécution. Si elle n’est pas compatible, `ReadClass` lancera un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Votre classe de temps d’exécution doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); sinon, `ReadClass` jettera un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Si *pSchema* est NULL, le schéma de la classe stockée peut être récupéré en appelant [CArchive::GetObjectSchema](#getobjectschema); autrement, <strong>\*</strong> *pSchema* contiendra le schéma de la classe de temps d’exécution qui a été précédemment stocké.

Vous pouvez utiliser [SerializeClass](#serializeclass) au lieu de `ReadClass`, qui gère à la fois la lecture et la rédaction de la référence de classe.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CArchive:WriteClass](#writeclass).

## <a name="carchivereadobject"></a><a name="readobject"></a>CArchive::LireObject

Lit les données de l’objet de l’archive et construit un objet du type approprié.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Paramètres

*pClasse*<br/>
Un pointeur constant à la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui correspond à l’objet que vous vous attendez à lire.

### <a name="return-value"></a>Valeur de retour

Un pointeur [CObject](../../mfc/reference/cobject-class.md) qui doit être jeté en toute sécurité à la classe dérivée correcte en utilisant [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Notes

Cette fonction est normalement `CArchive` appelée **>>** par l’extraction ( ) opérateur surchargé pour un pointeur [CObject.](../../mfc/reference/cobject-class.md) `ReadObject`, à son `Serialize` tour, appelle la fonction de la classe archivée.

Si vous fournissez un paramètre *pClass* nonzero, qui est obtenu par le [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) macro, alors la fonction vérifie la classe de temps d’exécution de l’objet archivé. Cela suppose que vous avez utilisé la macro IMPLEMENT_SERIAL dans la mise en œuvre de la classe.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CArchive:WriteObject](#writeobject).

## <a name="carchivereadstring"></a><a name="readstring"></a>CArchive::ReadString

Appelez cette fonction de membre pour lire les données `CArchive` de texte dans un tampon du fichier associé à l’objet.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Paramètres

*rString (en)*<br/>
Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contiendra la chaîne résultante après sa lecture à partir du fichier associé à l’objet CArchive.

*lpsz lpsz*<br/>
Spécifie un pointeur vers un tampon fourni par l’utilisateur qui recevra une chaîne de texte non terminée.

*Nmax*<br/>
Spécifie le nombre maximum de caractères à lire. Devrait être un de moins que la taille du tampon *lpsz.*

### <a name="return-value"></a>Valeur de retour

Dans la version qui renvoie BOOL, VRAI en cas de succès; FALSE autrement.

Dans la version `LPTSTR`qui renvoie un , un pointeur à la mémoire tampon contenant les données de texte; NULL si la fin du dossier a été atteinte.

### <a name="remarks"></a>Notes

Dans la version de la fonction membre avec le paramètre *nMax,* le tampon tiendra jusqu’à une limite de *nMax* - 1 caractères. La lecture est arrêtée par une paire d’alimentation de retour de voiture. Les personnages de la ligne neuve sont toujours supprimés. Un caractère nul ('0') est joint dans les deux cas.

[CArchive::Read](#read) est également disponible pour l’entrée en mode texte, mais il ne se termine pas sur une paire d’alimentation en ligne de retour de transport.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CArchive:WriteString](#writestring).

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>CArchive::SerializeClass

Appelez cette fonction de membre lorsque vous souhaitez stocker et charger les informations de version d’une classe de base.

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Paramètres

*pClassRef*<br/>
Un pointeur vers un objet de classe run-time pour la classe de base.

### <a name="remarks"></a>Notes

`SerializeClass`lit ou écrit la référence `CArchive` à une classe à `CArchive`l’objet, selon la direction de la . Utiliser `SerializeClass` à la place de [ReadClass](#readclass) et [WriteClass](#writeclass) comme un moyen pratique de sérialiser des objets de classe de base; `SerializeClass` nécessite moins de code et moins de paramètres.

Comme `ReadClass` `SerializeClass` , vérifie que les informations de classe archivées est compatible avec votre classe de temps d’exécution. Si elle n’est pas compatible, `SerializeClass` lancera un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Votre classe de temps d’exécution doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); sinon, `SerializeClass` jettera un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Utilisez la [macro RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) pour récupérer la valeur du paramètre *pRuntimeClass.* La classe de base doit avoir utilisé la [macro IMPLEMENT_SERIAL.](../../mfc/reference/run-time-object-model-services.md#implement_serial)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>CArchive::SetLoadParams

Appelez `SetLoadParams` lorsque vous allez lire un `CObject`grand nombre d’objets dérivés à partir d’une archive.

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Paramètres

*nGrowBy (en)*<br/>
Le nombre minimum de fentes d’élément à allouer si une augmentation de taille est nécessaire.

### <a name="remarks"></a>Notes

`CArchive`utilise un tableau de charge pour résoudre les références aux objets stockés dans l’archive. `SetLoadParams`vous permet de définir la taille à laquelle le tableau de charge se développe.

Vous ne `SetLoadParams` devez pas appeler après qu’un objet soit chargé, ou après [l’appel de MapObject](#mapobject) ou [ReadObject.](#readobject)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive::SetObjectSchema

Appelez cette fonction de membre pour définir le schéma d’objet stocké dans l’objet d’archives à *nSchema*.

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Paramètres

*nSchema (nSchema)*<br/>
Spécifie le schéma de l’objet.

### <a name="remarks"></a>Notes

Le prochain appel à [GetObjectSchema](#getobjectschema) retournera la valeur stockée dans *nSchema*.

Utilisation `SetObjectSchema` pour la version avancée; par exemple, lorsque vous souhaitez forcer une version `Serialize` particulière à être lue en fonction d’une classe dérivée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive::SetStoreParams

Utiliser `SetStoreParams` lors du stockage `CObject`d’un grand nombre d’objets dérivés dans une archive.

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Paramètres

*nHashSize (en)*<br/>
La taille de la table de hachage pour les cartes de pointeur d’interface. Devrait être un nombre premier.

*nBlockSize (en)*<br/>
Spécifie la granularité de la mémoire-allocation pour l’extension des paramètres. Devrait être une puissance de 2 pour la meilleure performance.

### <a name="remarks"></a>Notes

`SetStoreParams`vous permet de définir la taille de la table de hachage et la taille du bloc de la carte utilisée pour identifier les objets uniques pendant le processus de sérialisation.

Vous ne `SetStoreParams` devez pas appeler après que des objets sont stockés, ou après [l’appel de MapObject](#mapobject) ou [WriteObject.](#writeobject)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>CArchive::Écrire

Écrit un nombre spécifié d’octets à l’archive.

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Un pointeur vers un tampon fourni par l’utilisateur qui contient les données à écrire à l’archive.

*Nmax*<br/>
Un integer qui spécifie le nombre d’octets à écrire aux archives.

### <a name="remarks"></a>Notes

L’archive ne formate pas les octets.

Vous pouvez `Write` utiliser la `Serialize` fonction membre dans votre fonction pour écrire des structures ordinaires qui sont contenues dans vos objets.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>CArchive::WriteClass

Utilisez `WriteClass` pour stocker la version et les informations de classe d’une classe de base lors de la sérialisation de la classe dérivée.

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Paramètres

*pClassRef*<br/>
Un pointeur à la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui correspond à la référence de classe demandée.

### <a name="remarks"></a>Notes

`WriteClass`écrit une référence à la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) `CArchive`pour la classe de base à la . Utilisez [CArchive::ReadClass](#readclass) pour récupérer la référence.

`WriteClass`vérifie que les informations de classe archivées sont compatibles avec votre classe de temps d’exécution. Si elle n’est pas compatible, `WriteClass` lancera un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Votre classe de temps d’exécution doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); sinon, `WriteClass` jettera un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Vous pouvez utiliser [SerializeClass](#serializeclass) au lieu de `WriteClass`, qui gère à la fois la lecture et la rédaction de la référence de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>CArchive::WriteObject

Stocke `CObject` le spécifié à l’archive.

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*Pob*<br/>
Un pointeur constant de l’objet stocké.

### <a name="remarks"></a>Notes

Cette fonction est normalement `CArchive` appelée **<<** par l’opérateur `CObject`d’insertion () surchargé pour . `WriteObject`, à son `Serialize` tour, appelle la fonction de la classe archivée.

Vous devez utiliser la macro IMPLEMENT_SERIAL pour permettre l’archivage. `WriteObject`écrit le nom de classe ASCII aux archives. Ce nom de classe est validé plus tard pendant le processus de chargement. Un système spécial de codage empêche la duplication inutile du nom de classe pour plusieurs objets de la classe. Ce système empêche également le stockage redondant d’objets qui sont des cibles de plus d’un pointeur.

La méthode exacte d’encodage d’objets (y compris la présence du nom de classe ASCII) est un détail d’implémentation et pourrait changer dans les futures versions de la bibliothèque.

> [!NOTE]
> Terminez la création, la suppression et la mise à jour de tous vos objets avant de commencer à les archiver. Vos archives seront corrompues si vous mélangez l’archivage avec la modification de l’objet.

### <a name="example"></a>Exemple

Pour une définition `CAge`de la classe , voir l’exemple pour [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>CArchive::WriteString

Utilisez cette fonction de membre pour écrire des `CArchive` données à partir d’un tampon au fichier associé à l’objet.

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Paramètres

*lpsz lpsz*<br/>
Spécifie un pointeur à un tampon contenant une chaîne de texte non terminée.

### <a name="remarks"></a>Notes

Le caractère nul de fin ('0') n’est pas écrit au dossier; pas plus qu’une nouvelle ligne n’est automatiquement écrite.

`WriteString`jette une exception en réponse à plusieurs conditions, y compris l’état de disque-plein.

`Write`est également disponible, mais plutôt que de se mettre fin à un caractère nul, il écrit le nombre demandé d’octets au fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[CSocket, classe](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
