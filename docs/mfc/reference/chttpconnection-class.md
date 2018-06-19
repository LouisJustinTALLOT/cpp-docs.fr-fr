---
title: CHttpConnection, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
dev_langs:
- C++
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 808c88e3a98df12d35afa9ce207f57456520b169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367644"
---
# <a name="chttpconnection-class"></a>CHttpConnection, classe
Gère votre connexion à un serveur HTTP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHttpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHttpConnection::CHttpConnection](#chttpconnection)|Crée un objet `CHttpConnection`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CHttpConnection::OpenRequest](#openrequest)|Ouvre une requête HTTP.|  
  
## <a name="remarks"></a>Notes  
 HTTP est un des trois protocoles du serveur Internet implémentées par les classes WinInet MFC.  
  
 La classe `CHttpConnection` contient un constructeur et la fonction d’un seul membre, [OpenRequest](#openrequest), qui gère les connexions à un serveur avec un protocole HTTP.  
  
 Pour communiquer avec un serveur HTTP, vous devez d’abord créer une instance de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis créez un [objet CHttpConnection](#_mfc_chttpconnection) objet. Vous ne créez jamais un `CHttpConnection` directement l’objet ; au lieu de cela, appelez [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), qui crée le `CHttpConnection` de l’objet et retourne un pointeur vers elle.  
  
 Pour en savoir plus sur la façon `CHttpConnection` fonctionne avec les autres classes MFC Internet, consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur la connexion aux serveurs à l’aide de deux autres prises en charge les protocoles Internet, gopher et FTP, consultez les classes [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) et [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxinet.h  
  
##  <a name="chttpconnection"></a>  CHttpConnection::CHttpConnection  
 Cette fonction membre est appelée pour construire un `CHttpConnection` objet.  
  
```  
CHttpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    DWORD dwFlags,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Paramètres  
 `pSession`  
 Un pointeur vers un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet.  
  
 `hConnected`  
 Un handle à une connexion Internet.  
  
 `pstrServer`  
 Un pointeur vers une chaîne contenant le nom du serveur.  
  
 `dwContext`  
 L’identificateur de contexte pour le `CInternetConnection` objet. Consultez **remarques** pour plus d’informations sur `dwContext`.  
  
 `nPort`  
 Numéro qui identifie le port Internet pour cette connexion.  
  
 `pstrUserName`  
 Pointeur vers une chaîne se terminant par null qui spécifie le nom de l’utilisateur de se connecter. Si **NULL**, la valeur par défaut est anonyme.  
  
 `pstrPassword`  
 Un pointeur vers une chaîne se terminant par null qui spécifie le mot de passe à utiliser pour vous connecter. Si les deux `pstrPassword` et `pstrUserName` sont **NULL**, le mot de passe anonyme par défaut est le nom d’utilisateur par courrier électronique. Si `pstrPassword` est **NULL** (ou une chaîne vide), mais `pstrUserName` n’est pas **NULL**, un mot de passe vierge est utilisé. Le tableau suivant décrit le comportement pour les quatre paramètres possibles de `pstrUserName` et `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL** ou « »|**NULL** ou « »|« anonyme »|Nom de l’utilisateur par courrier électronique|  
|Non- **NULL** chaîne|**NULL** ou « »|`pstrUserName`|" "|  
|**NULL** Non - **NULL** chaîne|**ERREUR**|**ERREUR**||  
|Non- **NULL** chaîne|Non- **NULL** chaîne|`pstrUserName`|`pstrPassword`|  
  
 `dwFlags`  
 N’importe quelle combinaison de la **INTERNET_ FLAG_\***  indicateurs. Consultez le tableau dans le **remarques** section de [CHttpConnection::OpenRequest](#openrequest) pour obtenir une description de `dwFlags` valeurs.  
  
### <a name="remarks"></a>Notes  
 Vous ne créez jamais un `CHttpConnection` directement. Au lieu de cela, vous créez un objet en appelant [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).  
  
##  <a name="openrequest"></a>  CHttpConnection::OpenRequest  
 Appelez cette fonction membre pour ouvrir une connexion HTTP.  
  
```  
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

 
CHttpFile* OpenRequest(
    int nVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```  
  
### <a name="parameters"></a>Paramètres  
 `pstrVerb`  
 Un pointeur vers une chaîne contenant le verbe à utiliser dans la demande. Si `NULL`, « GET » est utilisé.  
  
 `pstrObjectName`  
 Un pointeur vers une chaîne contenant l’objet cible du verbe spécifié. Il s’agit généralement d’un nom de fichier, un module exécutable ou d’un spécificateur de recherche.  
  
 `pstrReferer`  
 Un pointeur vers une chaîne qui spécifie l’adresse (URL) du document à partir de laquelle l’URL dans la demande ( `pstrObjectName`) a été obtenu. Si `NULL`, aucun en-tête HTTP n’est spécifié.  
  
 `dwContext`  
 L’identificateur de contexte pour le `OpenRequest` opération. Consultez la section Notes pour plus d’informations `dwContext`.  
  
 `ppstrAcceptTypes`  
 Un pointeur vers un tableau se terminant par null de `LPCTSTR` des pointeurs vers des chaînes indiquant les types de contenu accepté par le client. Si `ppstrAcceptTypes` est `NULL`, les serveurs interprètent que le client accepte uniquement des documents de type « texte / * » (autrement dit, des documents texte uniquement et pas des images ou autres fichiers binaires). Le type de contenu est équivalent à la type_contenu variable CGI, qui identifie le type de données pour les requêtes que vous ont lié des informations, tels que HTTP POST et PUT.  
  
 `pstrVersion`  
 Pointeur vers une chaîne qui définit la version HTTP. Si `NULL`, « HTTP/1.0 » est utilisé.  
  
 `dwFlags`  
 N’importe quelle combinaison des indicateurs INTERNET_ FLAG_ *. Consultez la section Notes pour obtenir une description des possibles `dwFlags` valeurs.  
  
 `nVerb`  
 Un numéro associé au type de demande HTTP. Il peut s'agir d'une des valeurs suivantes :  
  
|Type de demande HTTP|Valeur `nVerb`|  
|-----------------------|-------------------|  
|`HTTP_VERB_POST`|0|  
|`HTTP_VERB_GET`|1|  
|`HTTP_VERB_HEAD`|2|  
|`HTTP_VERB_PUT`|3|  
|`HTTP_VERB_LINK`|4|  
|`HTTP_VERB_DELETE`|5|  
|`HTTP_VERB_UNLINK`|6|  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le [CHttpFile](../../mfc/reference/chttpfile-class.md) objet demandé.  
  
### <a name="remarks"></a>Notes  
 `dwFlags` peut avoir l'une des valeurs suivantes :  
  
|Indicateur d’Internet|Description|  
|-------------------|-----------------|  
|`INTERNET_FLAG_RELOAD`|Force un téléchargement du fichier demandé, un objet ou une liste de répertoires à partir du serveur d’origine, pas à partir du cache.|  
|`INTERNET_FLAG_DONT_CACHE`|N’ajoute pas l’entité retournée dans le cache.|  
|`INTERNET_FLAG_MAKE_PERSISTENT`|Ajoute l’entité retournée dans le cache comme une entité persistante. Cela signifie que le nettoyage du cache standard, la vérification de cohérence ou le garbage collection ne peut pas supprimer cet élément à partir du cache.|  
|`INTERNET_FLAG_SECURE`|Utilise une sémantique des transactions sécurisées. Cela se traduit par à l’aide de SSL/PCT et est uniquement explicite dans les demandes HTTP|  
|`INTERNET_FLAG_NO_AUTO_REDIRECT`|Utilisé uniquement avec HTTP, il spécifie que les redirections ne doivent pas être traitées automatiquement dans [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|  
  
 Remplacer la `dwContext` par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de la `CHttpConnection` objet créé par son [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet. La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec laquelle il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
 Exceptions peuvent être levées par cette fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
