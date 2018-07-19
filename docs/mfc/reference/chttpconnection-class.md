---
title: CHttpConnection, classe | Microsoft Docs
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
ms.openlocfilehash: 03e773e57b4cdaee09331dab651f41f1fa8db211
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336060"
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
 HTTP est un des trois protocoles de serveur Internet implémentées par les classes WinInet MFC.  
  
 La classe `CHttpConnection` contient un constructeur et une fonction d’un seul membre, [OpenRequest](#openrequest), qui gère les connexions à un serveur avec un protocole HTTP.  
  
 Pour communiquer avec un serveur HTTP, vous devez d’abord créer une instance de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis créez un [objet CHttpConnection](#_mfc_chttpconnection) objet. Vous ne créez jamais un `CHttpConnection` objet directement ; au lieu de cela, appelez [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), qui crée le `CHttpConnection` de l’objet et retourne un pointeur vers elle.  
  
 Pour en savoir plus sur la façon `CHttpConnection` fonctionne avec les autres classes Internet de MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur la connexion aux serveurs en utilisant les deux autres pris en charge les protocoles Internet, gopher et FTP, consultez les classes [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) et [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## <a name="requirements"></a>Configuration requise  
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
 *pSession*  
 Un pointeur vers un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet.  
  
 *hConnected*  
 Handle vers une connexion Internet.  
  
 *pstrServer*  
 Un pointeur vers une chaîne contenant le nom du serveur.  
  
 *dwContext*  
 L’identificateur de contexte pour le `CInternetConnection` objet. Consultez **remarques** pour plus d’informations sur *dwContext*.  
  
 *%nPort*  
 Nombre qui identifie le port Internet pour cette connexion.  
  
 *pstrUserName*  
 Pointeur vers une chaîne se terminant par null qui spécifie le nom de l’utilisateur pour vous connecter. Si NULL, la valeur par défaut est anonyme.  
  
 *pstrPassword*  
 Un pointeur vers une chaîne se terminant par null qui spécifie le mot de passe à utiliser pour vous connecter. Si les deux *pstrPassword* et *pstrUserName* ont la valeur NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL (ou une chaîne vide), mais *pstrUserName* n’est pas NULL, un mot de passe vide est utilisée. Le tableau suivant décrit le comportement pour les quatre paramètres possibles de *pstrUserName* et *pstrPassword*:  
  
|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|NULL ou « »|NULL ou « »|« anonyme »|Nom de messagerie de l’utilisateur|  
|Chaîne non NULL|NULL ou « »|*pstrUserName*|" "|  
|Chaîne Non-NULL NULL|ERREUR|ERREUR||  
|Chaîne non NULL|Chaîne non NULL|*pstrUserName*|*pstrPassword*|  
  
 *dwFlags*  
 N’importe quelle combinaison de la **INTERNET_ FLAG_\***  indicateurs. Consultez le tableau dans le **remarques** section de [CHttpConnection::OpenRequest](#openrequest) pour obtenir une description de *dwFlags* valeurs.  
  
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
 *pstrVerb*  
 Un pointeur vers une chaîne contenant le verbe à utiliser dans la demande. Si NULL, « GET » est utilisé.  
  
 *pstrObjectName*  
 Un pointeur vers une chaîne contenant l’objet cible du verbe spécifié. Cela est généralement un nom de fichier, d’un module exécutable ou d’un spécificateur de recherche.  
  
 *pstrReferer*  
 Un pointeur vers une chaîne qui spécifie l’adresse (URL) du document à partir de laquelle l’URL dans la demande ( *pstrObjectName*) a été obtenu. Si NULL, aucun en-tête HTTP n’est spécifié.  
  
 *dwContext*  
 L’identificateur de contexte pour le `OpenRequest` opération. Consultez la section Notes pour plus d’informations *dwContext*.  
  
 *ppstrAcceptTypes*  
 Un pointeur vers un tableau se terminant par null de pointeurs LPCTSTR en chaînes indiquant les types de contenu acceptés par le client. Si *ppstrAcceptTypes* est NULL, les serveurs interprètent que le client accepte uniquement les documents de type « texte / * » (autrement dit, les documents texte uniquement et pas images ou autres fichiers binaires). Le type de contenu est équivalent à la CONTENT_TYPE variable CGI, qui identifie le type de données pour les requêtes que vous ont lié des informations, telles que HTTP POST et PUT.  
  
 *pstrVersion*  
 Pointeur vers une chaîne définissant la version HTTP. Si NULL, « HTTP/1.0 » est utilisé.  
  
 *dwFlags*  
 N’importe quelle combinaison des indicateurs INTERNET_ FLAG_ *. Consultez la section Notes pour obtenir une description des possibles *dwFlags* valeurs.  
  
 *nVerb*  
 Un nombre associé au type de demande HTTP. Il peut s'agir d'une des valeurs suivantes :  
  
|Type de demande HTTP|*nVerb* valeur|  
|-----------------------|-------------------|  
|HTTP_VERB_POST|0|  
|HTTP_VERB_GET|1|  
|HTTP_VERB_HEAD|2|  
|HTTP_VERB_PUT|3|  
|HTTP_VERB_LINK|4|  
|HTTP_VERB_DELETE|5|  
|HTTP_VERB_UNLINK|6|  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le [CHttpFile](../../mfc/reference/chttpfile-class.md) objet demandé.  
  
### <a name="remarks"></a>Notes  
 *dwFlags* peut prendre l’une des opérations suivantes :  
  
|Indicateur d’Internet|Description|  
|-------------------|-----------------|  
|INTERNET_FLAG_RELOAD|Force un téléchargement du fichier demandé, un objet ou une liste de répertoires du serveur d’origine, pas à partir du cache.|  
|INTERNET_FLAG_DONT_CACHE|N’ajoute pas l’entité retournée au cache.|  
|INTERNET_FLAG_MAKE_PERSISTENT|Ajoute l’entité retournée dans le cache comme une entité persistante. Cela signifie que garbage collection, de la vérification de cohérence ou de nettoyage du cache standard ne peut pas supprimer cet élément à partir du cache.|  
|INTERNET_FLAG_SECURE|Utilise un sémantique de transaction. Cela se traduit par à l’aide de SSL/PCT et n’est significative que dans les requêtes HTTP|  
|INTERNET_FLAG_NO_AUTO_REDIRECT|Utilisé uniquement avec HTTP, il spécifie que les redirections ne doivent pas automatiquement gérées dans [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|  
  
 Remplacer le `dwContext` par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de la `CHttpConnection` objet créé par son [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet. La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
 Exceptions peuvent être levées avec cette fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
