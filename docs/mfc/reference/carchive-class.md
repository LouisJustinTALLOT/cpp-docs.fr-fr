---
title: CArchive (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f11edef585e699d90d8d33839e0e446cb5a726db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357535"
---
# <a name="carchive-class"></a>CArchive (classe)
Vous permet d’enregistrer un réseau complexe d’objets dans une forme binaire permanente (généralement stockage sur disque) qui persiste une fois ces objets sont supprimés.  
  
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
|[CArchive::Abort](#abort)|Ferme une archive sans lever d’exception.|  
|[CArchive::Close](#close)|Vide les données non écrites et se déconnecte de la `CFile`.|  
|[CArchive::Flush](#flush)|Vide les données non écrites à partir du tampon de l’archive.|  
|[CArchive::GetFile](#getfile)|Obtient le `CFile` pointeur d’objet pour cette archive.|  
|[CArchive::GetObjectSchema](#getobjectschema)|Appelée à partir de la `Serialize` fonction pour déterminer la version de l’objet qui est désérialisé.|  
|[CArchive::IsBufferEmpty](#isbufferempty)|Détermine si la mémoire tampon a été vidée pendant un Windows Sockets processus de réception.|  
|[CArchive::IsLoading](#isloading)|Détermine si l’archive se charge.|  
|[CArchive::IsStoring](#isstoring)|Détermine si l’archive est le stockage.|  
|[CArchive::MapObject](#mapobject)|Place des objets dans le mappage qui ne sont pas sérialisés dans le fichier, mais qui sont disponibles pour les sous-objets à référencer.|  
|[CArchive::Read](#read)|Lit les octets bruts.|  
|[CArchive::ReadClass](#readclass)|Lit une référence de classe précédemment stockée avec `WriteClass`.|  
|[CArchive::ReadObject](#readobject)|Appelle un objet `Serialize` fonction pour le chargement.|  
|[CArchive::ReadString](#readstring)|Lit une ligne unique de texte.|  
|[CArchive::SerializeClass](#serializeclass)|Lit ou écrit la référence de classe à la `CArchive` objet en fonction de la direction de la `CArchive`.|  
|[CArchive::SetLoadParams](#setloadparams)|Définit la taille à laquelle le groupe de charge augmente. Doit être appelée avant le chargement de tout objet ou avant `MapObject` ou `ReadObject` est appelée.|  
|[CArchive::SetObjectSchema](#setobjectschema)|Définit le schéma d’objet stocké dans l’objet de l’archive.|  
|[CArchive::SetStoreParams](#setstoreparams)|Définit la taille de table de hachage et la taille du bloc de la carte utilisée pour identifier les objets uniques pendant le processus de sérialisation.|  
|[CArchive::Write](#write)|Écrit les octets bruts.|  
|[CArchive::WriteClass](#writeclass)|Écrit une référence à la `CRuntimeClass` à la `CArchive`.|  
|[CArchive::WriteObject](#writeobject)|Appelle un objet `Serialize` fonction pour le stockage.|  
|[CArchive::WriteString](#writestring)|Écrit une seule ligne de texte.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CArchive::operator &lt;&lt;](#operator_lt_lt)|Stocke les objets et les types primitifs, à l’archive.|  
|[CArchive::operator &gt;&gt;](#operator_gt_gt)|Charge les types primitifs et les objets à partir de l’archive.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>Notes  
 `CArchive` ne dispose pas d’une classe de base.  
  
 Plus tard vous pouvez charger les objets à partir d’un stockage persistant, leur reconstitution en mémoire. Ce processus de rendre persistantes les données est appelé « sérialisation ».  
  
 Vous pouvez considérer un objet archive comme une sorte de flux binaire. Comme un flux d’entrée/sortie, une archive est associée à un fichier et permet la mise en mémoire tampon d’écriture et la lecture des données vers et depuis le stockage. Un flux d’entrée/sortie traite les séquences de caractères ASCII, mais une archive traite les données d’objet binaire dans un format non redondante efficace.  
  
 Vous devez créer un [CFile](../../mfc/reference/cfile-class.md) de l’objet avant de pouvoir créer un `CArchive` objet. En outre, vous devez vous assurer que l’état de chargement/stockage de l’archive est compatible avec le mode d’ouverture du fichier. Vous êtes limité à un archivage actif par fichier.  
  
 Lorsque vous construisez un `CArchive` de l’objet, vous l’attachez à un objet de classe `CFile` (ou une classe dérivée) qui représente un fichier ouvert. Vous spécifiez également si l’archive doit être utilisée pour le chargement ou le stockage. A `CArchive` objet peut traiter non seulement les types primitifs, mais également les objets de [CObject](../../mfc/reference/cobject-class.md)-conçus pour la sérialisation des classes dérivées. Une classe sérialisable a généralement une `Serialize` fonction membre et il utilise généralement le [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macros, comme indiqué dans la classe `CObject`.  
  
 L’extraction surchargée ( **>>**) et d’insertion ( **<<**) les opérateurs sont des interfaces de programmation d’archive pratique qui prennent en charge les deux types primitifs et `CObject` -les classes dérivées.  
  
 `CArchive` prend également en charge la programmation avec les classes MFC Windows Sockets [CSocket](../../mfc/reference/csocket-class.md) et [CSocketFile](../../mfc/reference/csocketfile-class.md). Le [IsBufferEmpty](#isbufferempty) fonction membre prend en charge que l’utilisation.  
  
 Pour plus d’informations sur `CArchive`, consultez les articles [sérialisation](../../mfc/serialization-in-mfc.md) et [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CArchive`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="abort"></a>  CArchive::Abort  
 Appelez cette fonction pour fermer l’archive sans lever d’exception.  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>Notes  
 Le **CArchive** normalement appel destructeur **fermer**, ce qui effacera toutes les données qui n’a pas été enregistrées à le `CFile` objet. Cela peut provoquer des exceptions.  
  
 Lorsque vous les interceptez ces exceptions, il est judicieux d’utiliser **abandonner**, de sorte que la destruction de le `CArchive` objet n’entraîne pas davantage les exceptions. Lors de la gestion des exceptions, `CArchive::Abort` pas lève une exception lors d’échecs de car, contrairement à [CArchive::Close](#close), **abandonner** ignore les échecs.  
  
 Si vous avez utilisé **nouveau** pour allouer la `CArchive` de l’objet sur le tas, vous devez le supprimer après la fermeture du fichier.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CArchive::WriteClass](#writeclass).  
  
##  <a name="carchive"></a>  CArchive::CArchive  
 Construit un `CArchive` de l’objet et indique si elle doit être utilisé pour le chargement ou le stockage d’objets.  
  
```  
CArchive(
    CFile* pFile,  
    UINT nMode,  
    int nBufSize = 4096,  
    void* lpBuf = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFile`  
 Un pointeur vers le `CFile` objet qui est la dernière source ou la destination des données persistantes.  
  
 `nMode`  
 Indicateur qui spécifie si les objets sont chargés à partir ou stockés dans l’archive. Le `nMode` paramètre doit avoir l’une des valeurs suivantes :  
  
- **CArchive::load** charge des données à partir de l’archive. Nécessite uniquement `CFile` une autorisation de lecture.  
  
- **CArchive::store** enregistre les données dans l’archive. Requiert `CFile` l’autorisation en écriture.  
  
- **CArchive::bNoFlushOnDelete** empêche l’archive d’appeler automatiquement `Flush` lorsque le destructeur d’archive est appelé. Si vous définissez cet indicateur, vous êtes chargé d’appeler explicitement **fermer** avant le destructeur est appelé. Si vous ne le faites pas, vos données sont endommagées.  
  
 `nBufSize`  
 Entier qui spécifie la taille de la mémoire tampon de fichier interne, en octets. Notez que la taille de mémoire tampon par défaut est 4 096 octets. Si vous archivez régulièrement des objets volumineux, vous améliore les performances si vous utilisez une taille de mémoire tampon plus importante est un multiple de la taille de mémoire tampon de fichier.  
  
 `lpBuf`  
 Un pointeur facultatif vers un tampon fourni par l’utilisateur de taille `nBufSize`. Si vous ne spécifiez pas ce paramètre, l’archivage alloue une mémoire tampon à partir du tas local et il libère lorsque l’objet est détruit. L’archive ne libère pas une mémoire tampon fournie par l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 Vous ne pouvez pas modifier cette spécification après avoir créé l’archive.  
  
 Vous ne pouvez pas utiliser `CFile` opérations de modifier l’état du fichier jusqu'à ce que vous avez fermé l’archive. Une telle opération va endommager l’intégrité de l’archive. Vous pouvez accéder à la position du pointeur de fichier à tout moment pendant la sérialisation en obtenant l’objet de fichier de l’archive à partir de la [GetFile](#getfile) fonction membre, puis en utilisant la [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) (fonction) . Vous devez appeler [CArchive::Flush](#flush) avant d’obtenir la position du pointeur de fichier.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="close"></a>  CArchive::Close  
 Vide toutes les données restantes dans la mémoire tampon et ferme l’archive se déconnecte de l’archive à partir du fichier.  
  
```  
void Close();
```  
  
### <a name="remarks"></a>Notes  
 Aucune autre opération sur l’archive n’est autorisées. Après avoir fermé une archive, vous pouvez créer une autre archive pour le même fichier, ou vous pouvez fermer le fichier.  
  
 La fonction membre **fermer** garantit que toutes les données sont transférées à partir de l’archive dans le fichier, et il rend l’archive indisponible. Pour terminer le transfert à partir du fichier vers le support de stockage, vous devez d’abord utiliser [CFile::Close](../../mfc/reference/cfile-class.md#close) , puis détruisez le `CFile` objet.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CArchive::WriteString](#writestring).  
  
##  <a name="flush"></a>  CArchive::Flush  
 Force toutes les données restantes dans la mémoire tampon d’archive à écrire dans le fichier.  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre `Flush` garantit que toutes les données est transféré à partir de l’archive dans le fichier. Vous devez appeler [CFile::Close](../../mfc/reference/cfile-class.md#close) pour achever le transfert à partir du fichier sur le support de stockage.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="getfile"></a>  CArchive::GetFile  
 Obtient le `CFile` pointeur d’objet pour cette archive.  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur constant vers le `CFile` objet en cours d’utilisation.  
  
### <a name="remarks"></a>Notes  
 Vous devez vider l’archive avant d’utiliser `GetFile`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="getobjectschema"></a>  CArchive::GetObjectSchema  
 Appelez cette fonction à partir de la `Serialize` fonction pour déterminer la version de l’objet qui est actuellement en cours de désérialisation.  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pendant la désérialisation, la version de l’objet en cours de lecture.  
  
### <a name="remarks"></a>Notes  
 Appel de cette fonction est valide uniquement lorsque le `CArchive` objet est en cours de chargement ( [CArchive::IsLoading](#isloading) retourne différente de zéro). Il doit être le premier appel dans le `Serialize` (fonction) et appelée une seule fois. La valeur de retour ( **UINT**) -1 indique que le numéro de version est inconnu.  
  
 A `CObject`-classe dérivée peut utiliser **VERSIONABLE_SCHEMA** combiné (à l’aide au niveau du bit `OR`) avec la version du schéma lui-même (dans le `IMPLEMENT_SERIAL` (macro)) pour créer un « objet de versionnables, », qui est un objet dont `Serialize` fonction membre peut lire plusieurs versions. La fonctionnalité de framework par défaut (sans **VERSIONABLE_SCHEMA**) consiste à lever une exception lorsque la version est incompatible.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="isbufferempty"></a>  CArchive::IsBufferEmpty  
 Appelez cette fonction membre pour déterminer si la mémoire tampon interne de l’objet de l’archive est vide.  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la mémoire tampon de l’archive est vide. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est fournie pour prendre en charge la programmation avec la classe MFC Windows Sockets `CSocketFile`. Vous n’avez pas besoin de l’utiliser pour un archivage associé à un `CFile` objet.  
  
 La raison de l’utilisation `IsBufferEmpty` avec une archive associée à un `CSocketFile` objet est que la mémoire tampon de l’archive peut contenir plusieurs messages ou enregistrement. Après avoir reçu un message, vous devez utiliser `IsBufferEmpty` pour contrôler une boucle qui continue à recevoir des données jusqu'à ce que la mémoire tampon est vide. Pour plus d’informations, consultez la [réception](../../mfc/reference/casyncsocket-class.md#receive) fonction membre de classe `CAsyncSocket`, qui montre comment utiliser `IsBufferEmpty`.  
  
 Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="isloading"></a>  CArchive::IsLoading  
 Détermine si l’archive de chargement des données.  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’archive est actuellement utilisée pour le chargement ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par le `Serialize` fonctions des classes archivées.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="isstoring"></a>  CArchive::IsStoring  
 Détermine si l’archive est le stockage des données.  
  
```  
BOOL IsStoring() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’archive est actuellement utilisée pour le stockage ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par le `Serialize` fonctions des classes archivées.  
  
 Si le `IsStoring` l’état d’une archive est différent de zéro, puis son `IsLoading` état est 0 et vice versa.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="mapobject"></a>  CArchive::MapObject  
 Appelez cette fonction membre pour placer des objets de la carte qui ne sont pas vraiment sérialisés dans le fichier, mais qui sont disponibles pour les sous-objets à référencer.  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Paramètres  
 `pOb`  
 Un pointeur constant vers l’objet stocké.  
  
### <a name="remarks"></a>Notes  
 Par exemple, vous ne pouvez pas sérialiser un document, mais vous devez sérialiser les éléments qui font partie du document. En appelant `MapObject`, vous autorisez les éléments ou les sous-objets, pour référencer le document. En outre, les sous-éléments sérialisés peuvent sérialiser leurs `m_pDocument` pointeur arrière.  
  
 Vous pouvez appeler `MapObject` lorsque vous de stocker et charger à partir de la `CArchive` objet. `MapObject` Ajoute l’objet spécifié aux structures de données interne conservées par le `CArchive` objet pendant la sérialisation et la désérialisation, mais contrairement à [ReadObject](#readobject) et [WriteObject](#writeobject) **,** il n’appelle pas sérialiser sur l’objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="m_pdocument"></a>  CArchive::m_pDocument  
 La valeur **NULL** par défaut, ce pointeur vers un **CDocument** peut être défini sur quoi que ce soit l’utilisateur de la `CArchive` souhaite disposer de l’instance.  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>Notes  
 Une utilisation courante de ce pointeur est pour transmettre des informations supplémentaires sur le processus de sérialisation à tous les objets en cours de sérialisation. Pour cela, l’initialisation du pointeur avec le document (un **CDocument**-classe dérivée) qui est en cours de sérialisation, de sorte que les objets dans le document peuvent accéder au document si nécessaire. Ce pointeur est également utilisé par `COleClientItem` objets pendant la sérialisation.  
  
 Les jeux de framework `m_pDocument` au document en cours de sérialisation lorsqu’un utilisateur émet un fichier ouvrir ou enregistrer des commandes. Si vous sérialisez un document conteneur objet de liaison et incorporation d’objets (OLE) pour des raisons autres que le fichier ouvrir ou enregistrer, vous devez définir explicitement `m_pDocument`. Par exemple, vous faites cela lors de la sérialisation d’un document conteneur dans le Presse-papiers.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="operator_lt_lt"></a>  CArchive::operator &lt;&lt;  
 Stocke l’objet indiqué ou un type primitif à l’archive.  
  
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
 A `CArchive` référence qui permet à plusieurs opérateurs d’insertion sur une seule ligne.  
  
### <a name="remarks"></a>Notes  
 Les deux dernières versions ci-dessus sont spécifiquement pour le stockage des entiers 64 bits.  
  
 Si vous avez utilisé le `IMPLEMENT_SERIAL` macro dans votre implémentation de la classe, puis l’opérateur d’insertion surchargés pour `CObject` appelle la méthode protégée **WriteObject**. Cette fonction, à son tour, appelle le `Serialize` fonction de la classe.  
  
 Le [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) opérateur d’insertion (<<) prend en charge le vidage de diagnostic et le stockage dans une archive.  
  
### <a name="example"></a>Exemple  
 Cet exemple illustre l’utilisation de la `CArchive` opérateur d’insertion << avec la `int` et `long` types.  
  
 [!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>Exemple  
 Cet exemple 2 illustre l’utilisation de la `CArchive` opérateur d’insertion << avec la `CStringT` type.  
  
 [!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="operator_gt_gt"></a>  CArchive::operator &gt;&gt;  
 Charge l’objet indiqué ou un type primitif à partir de l’archive.  
  
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
 A `CArchive` référence qui permet à plusieurs opérateurs d’extraction sur une seule ligne.  
  
### <a name="remarks"></a>Notes  
 Les deux dernières versions ci-dessus sont spécifiquement pour le chargement d’entiers 64 bits.  
  
 Si vous avez utilisé le `IMPLEMENT_SERIAL` macro dans votre implémentation de la classe, puis les opérateurs d’extraction surchargés pour `CObject` appeler la méthode protégée **ReadObject** (fonction) (avec un pointeur de la classe d’exécution différent de zéro). Cette fonction, à son tour, appelle le `Serialize` fonction de la classe.  
  
 Le [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) opérateur d’extraction (>>) prend en charge le chargement à partir d’une archive.  
  
### <a name="example"></a>Exemple  
 Cet exemple illustre l’utilisation de la `CArchive` opérateur d’extraction >> avec la `int` type.  
  
 [!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>Exemple  
 Cet exemple illustre l’utilisation de la `CArchive` opérateurs d’insertion et d’extraction <\< et >> avec la `CStringT` type.  
  
 [!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="read"></a>  CArchive::Read  
 Lit un nombre spécifié d’octets à partir de l’archive.  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpBuf`  
 Pointeur vers une mémoire tampon fournie par l’utilisateur qui doit recevoir les données lues à partir de l’archive.  
  
 `nMax`  
 Entier non signé spécifiant le nombre d’octets à lire à partir de l’archive.  
  
### <a name="return-value"></a>Valeur de retour  
 Entier non signé qui contient le nombre d’octets réellement lus. Si la valeur de retour est inférieur au nombre demandé, la fin du fichier a été atteint. Aucune exception n’est levée sur la condition de fin de fichier.  
  
### <a name="remarks"></a>Notes  
 L’archive n’interprète pas les octets.  
  
 Vous pouvez utiliser la **en lecture** fonction membre au sein de votre `Serialize` fonction pour la lecture des structures ordinaires qui sont contenus dans vos objets.  
  
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
 `pClassRefRequested`  
 Un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure qui correspond à la référence de la classe demandée. Peut être **NULL**.  
  
 `pSchema`  
 Pointeur vers un schéma de la classe d’exécution précédemment stocké.  
  
 `pObTag`  
 Nombre qui fait référence à la balise d’unique d’un objet. Utilisé en interne par l’implémentation de [ReadObject](#readobject). Exposé pour la programmation avancée uniquement ; `pObTag` qu’elle devrait normalement être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure.  
  
### <a name="remarks"></a>Notes  
 Si `pClassRefRequested` n’est pas **NULL**, `ReadClass` vérifie que les informations de classe archivée sont compatibles avec votre classe d’exécution. S’il n’est pas compatible, `ReadClass` lèvera une [exception CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Votre classe runtime doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); sinon, `ReadClass` lèvera une [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Si `pSchema` est **NULL**, le schéma de la classe stockée peut être récupéré en appelant [CArchive::GetObjectSchema](#getobjectschema); sinon, **\*** `pSchema`contiendra le schéma de la classe d’exécution qui a été précédemment enregistré.  
  
 Vous pouvez utiliser [SerializeClass](#serializeclass) au lieu de `ReadClass`, qui gère la lecture et l’écriture de la référence de classe.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CArchive::WriteClass](#writeclass).  
  
##  <a name="readobject"></a>  CArchive::ReadObject  
 Lit les données de l’objet à partir de l’archive et construit un objet du type approprié.  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Paramètres  
 `pClass`  
 Un pointeur constant vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure qui correspond à l’objet que vous vous attendez à lire.  
  
### <a name="return-value"></a>Valeur de retour  
 A [CObject](../../mfc/reference/cobject-class.md) pointeur qui doit être casté en toute sécurité correct de classe dérivée à l’aide de [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée par le `CArchive` extraction ( **>>**) opérateur surchargé pour un [CObject](../../mfc/reference/cobject-class.md) pointeur. **ReadObject**, à son tour, appelle le `Serialize` fonction de la classe archivée.  
  
 Si vous fournissez un autre que zéro `pClass` paramètre, qui est obtenue par la [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) (macro), puis la fonction vérifie la classe d’exécution de l’objet archivé. Cela suppose que vous avez utilisé le `IMPLEMENT_SERIAL` macro dans l’implémentation de la classe.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CArchive::WriteObject](#writeobject).  
  
##  <a name="readstring"></a>  CArchive::ReadString  
 Appelez cette fonction membre pour lire les données de texte dans une mémoire tampon à partir du fichier associé à le `CArchive` objet.  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>Paramètres  
 `rString`  
 Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient la chaîne résultante après qu’il est lu à partir du fichier associé à l’objet CArchive.  
  
 `lpsz`  
 Spécifie un pointeur vers une mémoire tampon fournie par l’utilisateur qui recevra une chaîne de texte de se terminant par null.  
  
 `nMax`  
 Spécifie le nombre maximal de caractères à lire. Doit être un inférieur à la taille de la *lpsz* mémoire tampon.  
  
### <a name="return-value"></a>Valeur de retour  
 Dans la version retourne **BOOL**, **TRUE** en cas de réussite ; **FALSE** dans le cas contraire.  
  
 Dans la version qui retourne un `LPTSTR`, un pointeur vers la mémoire tampon qui contient les données texte ; **NULL** si la fin du fichier a été atteinte.  
  
### <a name="remarks"></a>Notes  
 Dans la version de la fonction membre avec le `nMax` paramètre, la mémoire tampon contiendra à une limite de `nMax` - 1 caractères. La lecture est arrêtée par une paire de sauts de ligne de transport. Caractères de saut de ligne de fin sont toujours supprimés. Un caractère null ('\0') est ajouté dans les deux cas.  
  
 [CArchive::Read](#read) est également disponible pour les entrées en mode texte, mais il n’arrête pas sur une paire de sauts de ligne de transport.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CArchive::WriteString](#writestring).  
  
##  <a name="serializeclass"></a>  CArchive::SerializeClass  
 Appelez cette fonction membre lorsque vous souhaitez stocker et charger les informations de version de classe de base.  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Paramètres  
 `pClassRef`  
 Pointeur vers un objet de classe d’exécution pour la classe de base.  
  
### <a name="remarks"></a>Notes  
 `SerializeClass` lit ou écrit la référence à une classe pour le `CArchive` objet, en fonction de la direction de la `CArchive`. Utilisez `SerializeClass` à la place de [ReadClass](#readclass) et [WriteClass](#writeclass) comme un moyen pratique pour sérialiser des objets de classe de base ; `SerializeClass` nécessite moins de code et moins de paramètres.  
  
 Comme `ReadClass`, `SerializeClass` vérifie que les informations de classe archivée sont compatibles avec votre classe d’exécution. S’il n’est pas compatible, `SerializeClass` lèvera une [exception CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Votre classe runtime doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); sinon, `SerializeClass` lèvera une [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Utilisez le [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) macro pour récupérer la valeur pour le `pRuntimeClass` paramètre. La classe de base doit avoir utilisé le [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) (macro).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="setloadparams"></a>  CArchive::SetLoadParams  
 Appelez `SetLoadParams` lorsque vous vous apprêtez à lire un grand nombre de `CObject`-objets dérivés à partir d’une archive.  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>Paramètres  
 `nGrowBy`  
 Le nombre minimal d’emplacements d’élément pour allouer si une augmentation de la taille n’est nécessaire.  
  
### <a name="remarks"></a>Notes  
 `CArchive` utilise un tableau de charge pour résoudre les références aux objets stockés dans l’archive. `SetLoadParams` vous permet de définir la taille à laquelle le groupe de charge augmente.  
  
 Vous ne devez pas appeler `SetLoadParams` après le chargement de n’importe quel objet, ou après [MapObject](#mapobject) ou [ReadObject](#readobject) est appelée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="setobjectschema"></a>  CArchive::SetObjectSchema  
 Appelez cette fonction membre pour définir le schéma d’objet stocké dans l’objet de l’archive à `nSchema`.  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>Paramètres  
 `nSchema`  
 Spécifie le schéma de l’objet.  
  
### <a name="remarks"></a>Notes  
 L’appel suivant à [GetObjectSchema](#getobjectschema) retournera la valeur stockée dans `nSchema`.  
  
 Utilisez `SetObjectSchema` pour le contrôle de version avancée ; par exemple, lorsque vous voulez forcer une version particulière à lire dans un `Serialize` fonction d’une classe dérivée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="setstoreparams"></a>  CArchive::SetStoreParams  
 Utilisez `SetStoreParams` lors du stockage d’un grand nombre de `CObject`-dérivées des objets dans une archive.  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>Paramètres  
 *nHashSize*  
 La taille de la table de hachage pour le pointeur d’interface est mappé. Doit être un nombre premier.  
  
 `nBlockSize`  
 Spécifie la granularité d’allocation de mémoire pour l’extension des paramètres. Doit être une puissance de 2 pour des performances optimales.  
  
### <a name="remarks"></a>Notes  
 `SetStoreParams` vous permet de définir la taille de table de hachage et la taille du bloc de la carte utilisée pour identifier les objets uniques pendant le processus de sérialisation.  
  
 Vous ne devez pas appeler `SetStoreParams` une fois que tous les objets sont stockés, ou après [MapObject](#mapobject) ou [WriteObject](#writeobject) est appelée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="write"></a>  CArchive::Write  
 Écrit un nombre spécifié d’octets dans l’archive.  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpBuf`  
 Pointeur vers une mémoire tampon fournie par l’utilisateur qui contient les données à écrire dans l’archive.  
  
 `nMax`  
 Entier qui spécifie le nombre d’octets à écrire dans l’archive.  
  
### <a name="remarks"></a>Notes  
 L’archive ne met pas en forme les octets.  
  
 Vous pouvez utiliser la **écrire** fonction membre au sein de votre `Serialize` fonction d’écriture ordinaire structures qui sont contenus dans vos objets.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="writeclass"></a>  CArchive::WriteClass  
 Utilisez `WriteClass` pour stocker les informations de version et de la classe d’une classe de base lors de la sérialisation de la classe dérivée.  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Paramètres  
 `pClassRef`  
 Un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure qui correspond à la référence de la classe demandée.  
  
### <a name="remarks"></a>Notes  
 `WriteClass` écrit une référence à la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pour la classe de base pour le `CArchive`. Utilisez [CArchive::ReadClass](#readclass) pour récupérer la référence.  
  
 `WriteClass` vérifie que les informations de classe archivée sont compatibles avec votre classe d’exécution. S’il n’est pas compatible, `WriteClass` lèvera une [exception CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Votre classe runtime doit utiliser [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); sinon, `WriteClass` lèvera une [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Vous pouvez utiliser [SerializeClass](#serializeclass) au lieu de `WriteClass`, qui gère la lecture et l’écriture de la référence de classe.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="writeobject"></a>  CArchive::WriteObject  
 Stocke le texte spécifié `CObject` à l’archive.  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Paramètres  
 `pOb`  
 Un pointeur constant vers l’objet stocké.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée par le `CArchive` insertion ( **<<**) opérateur surchargé pour `CObject`. **WriteObject**, à son tour, appelle le `Serialize` fonction de la classe archivée.  
  
 Vous devez utiliser le `IMPLEMENT_SERIAL` macro pour activer l’archivage. **WriteObject** écrit le nom de classe ASCII à l’archive. Nom de la classe est validé ultérieurement pendant le processus de chargement. Un schéma d’encodage spécial empêche la duplication de nom de classe pour plusieurs objets de la classe. Ce schéma empêche également un stockage redondant d’objets qui sont les cibles de plusieurs pointeurs.  
  
 L’objet exact de codage (méthode) (y compris la présence de la classe ASCII) est un détail d’implémentation et peut changer dans les futures versions de la bibliothèque.  
  
> [!NOTE]
>  Terminer la création, la suppression et la mise à jour de tous vos objets avant de commencer à les archiver. Votre archivage soient endommagée si vous combinez l’archivage et la modification de l’objet.  
  
### <a name="example"></a>Exemple  
 Pour une définition de la classe `CAge`, consultez l’exemple de [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).  
  
 [!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="writestring"></a>  CArchive::WriteString  
 Utilisez cette fonction membre pour écrire des données à partir d’une mémoire tampon dans le fichier associé à le `CArchive` objet.  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpsz`  
 Spécifie un pointeur vers une mémoire tampon contenant une chaîne de texte de se terminant par null.  
  
### <a name="remarks"></a>Notes  
 Le caractère null de fin ('\0') n’est pas écrite dans le fichier. ni est un saut de ligne est automatiquement écrite.  
  
 `WriteString` lève une exception en réponse à plusieurs conditions, y compris la condition de disque plein.  
  
 **Écrire** est également disponible, mais au lieu de se terminent un caractère null, elle écrit le nombre d’octets demandé dans le fichier.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CFile (classe)](../../mfc/reference/cfile-class.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [CSocket (classe)](../../mfc/reference/csocket-class.md)   
 [CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
