---
title: Classe CDebugReportHook | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
dev_langs: C++
helpviewer_keywords: CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: df098ee80bcd8fa81b5503cc21b08ded86945a72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook (classe)
Cette classe permet d’envoyer des rapports de débogage à un canal nommé.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CDebugReportHook
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Appels [SetPipeName](#setpipename), [SetTimeout](#settimeout), et [SetHook](#sethook).|  
|[CDebugReportHook :: ~ CDebugReportHook](#dtor)|Appels [CDebugReportHook::RemoveHook](#removehook).|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statique) La fonction personnalisée qui est liée à la durée d’exécution C déboguer des processus de création de rapports.|  
|[CDebugReportHook::RemoveHook](#removehook)|Appelez cette méthode pour arrêter l’envoi de rapports de débogage pour le canal nommé et de restauration le raccordement de rapport précédente.|  
|[CDebugReportHook::SetHook](#sethook)|Appelez cette méthode pour déclencher l’envoi des rapports de débogage pour le canal nommé.|  
|[CDebugReportHook::SetPipeName](#setpipename)|Appelez cette méthode pour définir l’ordinateur et le nom du canal auquel les rapports de débogage seront envoyés.|  
|[CDebugReportHook::SetTimeout](#settimeout)|Appelez cette méthode pour définir le délai en millisecondes que cette classe attend la fin du canal nommé soit disponible.|  
  
## <a name="remarks"></a>Notes  
 Créer une instance de cette classe dans les versions debug de vos services ou applications pour envoyer les rapports de débogage à un canal nommé. Rapports de débogage sont générés en appelant [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) ou à l’aide d’un wrapper pour cette fonction comme le [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) et [ATLASSERT ;](debugging-and-error-reporting-macros.md#atlassert) macros.  
  
 Utilisation de cette classe vous permet de déboguer interactivement des composants en cours d’exécution non interactif [stations de fenêtre](http://msdn.microsoft.com/library/windows/desktop/ms687096).  
  
 Notez que les rapports de débogage sont envoyés en utilisant le contexte de sécurité sous-jacente du thread. L’emprunt d’identité est temporairement désactivé afin que les rapports de débogage peuvent être affichés dans les situations où l’emprunt d’identité des utilisateurs de faibles a eu lieu, comme dans les applications web.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlutil.h  
  
##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook  
 Appels [SetPipeName](#setpipename), [SetTimeout](#settimeout), et [SetHook](#sethook).  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `szMachineName`  
 Le nom de l’ordinateur auquel la sortie de débogage doit être envoyée. Par défaut, l’ordinateur local.  
  
 `szPipeName`  
 Le nom du canal nommé auquel la sortie de débogage doit être envoyée.  
  
 `dwTimeout`  
 La durée en millisecondes que cette classe attend la fin du canal nommé soit disponible.  
  
##  <a name="dtor"></a>CDebugReportHook :: ~ CDebugReportHook  
 Appels [CDebugReportHook::RemoveHook](#removehook).  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc  
 La fonction personnalisée qui est liée à la durée d’exécution C déboguer des processus de création de rapports.  
  
```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `reportType`  
 Le type de rapport (_CRT_WARN, _CRT_ERROR ou _CRT_ASSERT).  
  
 `message`  
 La chaîne de message.  
  
 *returnValue*  
 La valeur doit être retournée par [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne FALSE si le raccordement gère intégralement le message concerné et qu’aucun rapport supplémentaire n’est requis. Retourne la valeur TRUE si `_CrtDbgReport` doit signaler le message de façon normale.  
  
### <a name="remarks"></a>Notes  
 La fonction de création de rapports tente d’ouvrir le canal nommé et communiquer avec le processus à l’autre extrémité. Si le canal est occupé, la fonction de création de rapports attend que le canal est disponible ou l’expiration du délai. Le délai d’attente peut être définie par le constructeur ou un appel à [CDebugReportHook::SetTimeout](#settimeout).  
  
 Le code de cette fonction est exécuté dans le contexte de sécurité sous-jacente du thread appelant, autrement dit, l’emprunt d’identité est désactivé pendant la durée de cette fonction.  
  
##  <a name="removehook"></a>CDebugReportHook::RemoveHook  
 Appelez cette méthode pour arrêter l’envoi de rapports de débogage pour le canal nommé et de restauration le raccordement de rapport précédente.  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>Notes  
 Appels [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) pour restaurer le raccordement de rapport précédente.  
  
##  <a name="sethook"></a>CDebugReportHook::SetHook  
 Appelez cette méthode pour déclencher l’envoi des rapports de débogage pour le canal nommé.  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>Notes  
 Appels [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) des rapports de débogage routés via [CDebugReportHookProc](#cdebugreporthookproc) au canal nommé. Cette classe effectue le suivi de la précédente raccordement de rapport afin qu’il puisse être restaurées si [RemoveHook](#removehook) est appelée.  
  
##  <a name="setpipename"></a>CDebugReportHook::SetPipeName  
 Appelez cette méthode pour définir l’ordinateur et le nom du canal auquel les rapports de débogage seront envoyés.  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `szMachineName`  
 Le nom de l’ordinateur auquel la sortie de débogage doit être envoyée.  
  
 `szPipeName`  
 Le nom du canal nommé auquel la sortie de débogage doit être envoyée.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="settimeout"></a>CDebugReportHook::SetTimeout  
 Appelez cette méthode pour définir le délai en millisecondes que cette classe attend la fin du canal nommé soit disponible.  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwTimeout`  
 La durée en millisecondes que cette classe attend la fin du canal nommé soit disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../atl/reference/atl-classes.md)
