---
title: Classe de CStdioFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
dev_langs:
- C++
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89de8dddae6d6549fe12086b84e6bb656afcbc4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374986"
---
# <a name="cstdiofile-class"></a>Classe de CStdioFile
Représente un fichier de flux d’exécution C tel qu’il est ouvert par la fonction de l’exécution [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStdioFile : public CFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](#cstdiofile)|Construit un `CStdioFile` objet à partir d’un pointeur de fichier ou chemin d’accès.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CStdioFile::Open](#open)|Surchargé. Ouvrir est conçu pour une utilisation avec la valeur par défaut `CStdioFile` constructeur (remplace [CFile::Open](../../mfc/reference/cfile-class.md#open)).|  
|[CStdioFile::ReadString](#readstring)|Lit une ligne unique de texte.|  
|[CStdioFile::Seek](#seek)|Positionne le pointeur de fichier actuel.|  
|[CStdioFile::WriteString](#writestring)|Écrit une seule ligne de texte.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStdioFile::m_pStream](#m_pstream)|Contient un pointeur vers un fichier ouvert.|  
  
## <a name="remarks"></a>Notes  
 Fichiers de flux de données sont en mémoire tampon et peuvent être ouvert en mode de texte (la valeur par défaut) ou en mode binaire.  
  
 Mode texte fournit un traitement spécial des paires chariot / sauts de ligne. Lorsque vous écrivez un saut de ligne (0x0A) de caractères pour un mode texte `CStdioFile` (objet), la paire d’octets (0x0D, 0x0A) est envoyé dans le fichier. Lors de la lecture, la paire d’octets (0x0D, 0x0A) est convertie en un seul octet 0x0A.  
  
 Le [CFile](../../mfc/reference/cfile-class.md) fonctions [dupliquer](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), et [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) ne sont pas pris en charge pour `CStdioFile`.  
  
 Si vous appelez ces fonctions sur un `CStdioFile`, vous obtenez un [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Pour plus d’informations sur l’utilisation de `CStdioFile`, consultez les articles [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans les *Run-Time Library Reference*.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile  
 Construit et initialise un objet `CStdioFile`.  
  
```  
CStdioFile();  
CStdioFile(CAtlTransactionManager* pTM);  
  CStdioFile(FILE* pOpenStream);

 
CStdioFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags);

 
CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>Paramètres  
 `pOpenStream`  
 Spécifie le pointeur de fichier retourné par un appel à la fonction d’exécution C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 `lpszFileName`  
 Spécifie une chaîne qui est le chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu.  
  
 `nOpenFlags`  
 Spécifie les options pour la création d’un fichier, le partage de fichiers et les modes d’accès au fichier. Vous pouvez spécifier plusieurs options à l’aide de l’opération de bits OR ( `|`) (opérateur).  
  
 Une option de mode d’accès fichier est requise ; autres modes sont facultatifs. Consultez [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) pour obtenir la liste des options de mode et d’autres indicateurs. Dans les MFC version 3.0 et versions ultérieure, les indicateurs de partage sont autorisées.  
  
 `pTM`  
 Pointeur vers l’objet CAtlTransactionManager.  
  
### <a name="remarks"></a>Notes  
 Le constructeur par défaut ne s’attache pas un fichier à la `CStdioFile` objet. Lorsque vous utilisez ce constructeur, vous devez utiliser le `CStdioFile::Open` méthode pour ouvrir un fichier et l’attacher à la `CStdioFile` objet.  
  
 Le constructeur à paramètre unique attache un flux de fichier ouvert dans le `CStdioFile` objet. Autorisé les valeurs de pointeur sont les pointeurs de fichier d’entrée/sortie prédéfinie `stdin`, `stdout`, ou `stderr`.  
  
 Le constructeur de deux paramètres crée un `CStdioFile` de l’objet et ouvre le fichier correspondant avec le chemin d’accès donné.  
  
 Si vous passez `NULL` pour soit `pOpenStream` ou `lpszFileName`, le constructeur lève une `CInvalidArgException*`.  
  
 Si le fichier ne peut pas être ouvert ou créé, le constructeur lève une `CFileException*`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]  
  
##  <a name="m_pstream"></a>  CStdioFile::m_pStream  
 Le `m_pStream` membre de données est le pointeur vers un fichier ouvert, tel que retourné par la fonction d’exécution C `fopen`.  
  
```  
FILE* m_pStream;  
```  
  
### <a name="remarks"></a>Notes  
 Il s’agit de **NULL** si le fichier n’a jamais été ouvert ou a été fermé.  
  
##  <a name="open"></a>  CStdioFile::Open  
 Surchargé. Ouvrir est conçu pour une utilisation avec la valeur par défaut `CStdioFile` constructeur.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CAtlTransactionManager* pTM,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFileName`  
 Chaîne qui est le chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu.  
  
 `nOpenFlags`  
 Mode de partage et d’accès. Spécifie l’action à entreprendre lors de l’ouverture du fichier. Vous pouvez combiner des options à l’aide de l’opération de bits OR (&#124;) (opérateur). Autorisation d’accès un à et un seul partage sont requis ; les modes modeCreate et modeNoInherit sont facultatifs.  
  
 `pError`  
 Pointeur vers un objet d’exception du fichier existant qui recevra l’état d’une opération ayant échoué.  
  
 `pTM`  
 Pointeur vers un `CAtlTransactionManager` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` en cas de réussite ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="readstring"></a>  CStdioFile::ReadString  
 Lit les données de texte dans une mémoire tampon, jusqu'à une limite de `nMax`-1 caractères, à partir du fichier associé à le `CStdioFile` objet.  
  
```  
virtual LPTSTR ReadString(
    LPTSTR lpsz,  
    UINT nMax);  
  
virtual BOOL ReadString(CString& rString);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpsz`  
 Spécifie un pointeur vers une mémoire tampon fournie par l’utilisateur qui recevra une chaîne de texte de se terminant par null.  
  
 `nMax`  
 Spécifie le nombre maximal de caractères à lire, sans compter le caractère null de fin.  
  
 `rString`  
 Une référence à un `CString` objet qui contient la chaîne lorsque la fonction retourne.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la mémoire tampon contenant les données texte. **NULL** si la fin du fichier a été atteinte sans lors de la lecture des données ; ou si la valeur booléenne **FALSE** si la fin du fichier a été atteinte sans lors de la lecture des données.  
  
### <a name="remarks"></a>Notes  
 La lecture est arrêtée par le premier caractère de saut de ligne. Si, dans ce cas, moins de `nMax`-1 caractères ont été lus, un caractère de saut de ligne est stocké dans la mémoire tampon. Un caractère null ('\0') est ajouté dans les deux cas.  
  
 [CFile::Read](../../mfc/reference/cfile-class.md#read) est également disponible pour les entrées en mode texte, mais il n’arrête pas sur une paire de sauts de ligne de transport.  
  
> [!NOTE]
>  Le `CString` version de cette fonction supprime le `'\n'` le cas échéant ; le `LPTSTR` n’est pas le cas de version.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]  
  
##  <a name="seek"></a>  CStdioFile::Seek  
 Repositionne le pointeur dans un fichier déjà ouvert.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOff,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Paramètres  
 `lOff`  
 Nombre d’octets pour déplacer le pointeur.  
  
 `nFrom`  
 Mode de déplacement du pointeur. Doit être une des valeurs suivantes :  
  
- `CFile::begin`: Déplacer le pointeur de fichier `lOff` octets transférer à partir du début du fichier.  
  
- `CFile::current`: Déplacer le pointeur de fichier `lOff` octets à partir de la position actuelle dans le fichier.  
  
- `CFile::end`: Déplacer le pointeur de fichier `lOff` octets à partir de la fin du fichier. Notez que `lOff` doivent être négatif à rechercher dans l’objet existant de fichiers ; positif de valeurs de recherche au-delà de la fin du fichier.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la position demandée est conforme, `Seek` retourne l’offset d’octet à partir du début du fichier. Sinon, la valeur de retour n’est pas définie et un `CFileException` objet est levé.  
  
### <a name="remarks"></a>Notes  
 Le `Seek` fonction permet un accès aléatoire pour le contenu d’un fichier en déplaçant le pointeur un montant spécifié, relative ou absolue. Aucune donnée n’est lue pendant la recherche. Si la position demandée est supérieure à la taille du fichier, la longueur du fichier sera étendue à cette position, et aucune exception n’est levée.  
  
 Lorsqu’un fichier est ouvert, le pointeur de fichier est positionné à l’offset 0, le début du fichier.  
  
 Cette implémentation de `Seek` est basée sur la fonction de la bibliothèque Runtime (CRT) `fseek`. Il existe plusieurs limites sur l’utilisation de `Seek` sur les flux ouverts en mode texte. Pour plus d’informations, consultez [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser `Seek` pour déplacer le pointeur de 1 000 octets à partir du début de la `cfile` fichier. Notez que `Seek` ne lit pas les données, vous devez appeler ensuite [CStdioFile::ReadString](#readstring) pour lire les données.  
  
 [!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]  
  
##  <a name="writestring"></a>  CStdioFile::WriteString  
 Écrit des données à partir d’une mémoire tampon dans le fichier associé à le `CStdioFile` objet.  
  
```  
virtual void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpsz`  
 Spécifie un pointeur vers une mémoire tampon qui contient une chaîne se terminant par null.  
  
### <a name="remarks"></a>Notes  
 Le caractère null de fin ( `\0`) n’est pas écrite dans le fichier. Cette méthode écrit des caractères de saut de ligne `lpsz` vers le fichier comme une paire retour chariot de transport.  
  
 Si vous souhaitez écrire des données qui ne sont pas terminée dans un fichier, utilisez `CStdioFile::Write` ou [CFile::Write](../../mfc/reference/cfile-class.md#write).  
  
 Cette méthode lève un `CInvalidArgException*` si vous spécifiez `NULL` pour la `lpsz` paramètre.  
  
 Cette méthode lève un `CFileException*` en réponse aux erreurs de système de fichiers.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CFile (classe)](../../mfc/reference/cfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CFile (classe)](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)   
 [CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)   
 [CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)   
 [CNotSupportedException, classe](../../mfc/reference/cnotsupportedexception-class.md)
