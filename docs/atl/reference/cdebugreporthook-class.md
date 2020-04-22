---
title: Classe CDebugReportHook
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 8380556bbe007326156bf0ec0eefc23052e8e056
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747724"
---
# <a name="cdebugreporthook-class"></a>Classe CDebugReportHook

Utilisez cette classe pour envoyer des rapports de débogé à un tuyau nommé.

## <a name="syntax"></a>Syntaxe

```
class CDebugReportHook
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Appels [SetPipeName](#setpipename), [SetTimeout](#settimeout), et [SetHook](#sethook).|
|[CDebugReportHook::CDebugReportHook](#dtor)|Appels [CDebugReportHook::RemoveHook](#removehook).|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statique) La fonction de déclaration personnalisée qui est accrochée au processus de déclaration de débaillement C run-time.|
|[CDebugReportHook::RemoveHook](#removehook)|Appelez cette méthode pour arrêter d’envoyer des rapports de déboçon à la pipe nommée et restaurer le crochet de rapport précédent.|
|[CDebugReportHook::SetHook](#sethook)|Appelez cette méthode pour commencer à envoyer des rapports de déboçon à la pipe nommée.|
|[CDebugReportHook::SetPipeName](#setpipename)|Appelez cette méthode pour régler la machine et le nom du tuyau auquel les rapports de débogé seront envoyés.|
|[CDebugReportHook::SetTimeout](#settimeout)|Appelez cette méthode pour régler le temps en millisecondes que cette classe attendra que le tuyau nommé devienne disponible.|

## <a name="remarks"></a>Notes

Créez un exemple de cette classe dans la construction de débog de vos services ou applications pour envoyer des rapports de débbug à un tuyau nommé. Les rapports Debug sont générés en appelant [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) ou en utilisant un emballage pour cette fonction tels que les macros [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) et [ATLASSERT.](debugging-and-error-reporting-macros.md#atlassert)

L’utilisation de cette classe vous permet de déboguer interactivement les composants en cours d’exécution dans [les stations](/windows/win32/winstation/window-stations)de fenêtre non interactives .

Notez que les rapports de débogé sont envoyés en utilisant le contexte de sécurité sous-jacent du thread. L’usurpation d’identité est temporairement désactivée de sorte que les rapports de déboçon peuvent être consultés dans les situations où l’usurpation d’identité des utilisateurs de privilège faible a lieu, comme dans les applications Web.

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

Appels [SetPipeName](#setpipename), [SetTimeout](#settimeout), et [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Paramètres

*szMachineName (en)*<br/>
Le nom de la machine à laquelle la sortie de débogé doit être envoyée. Par défaut à la machine locale.

*szPipeName (en)*<br/>
Le nom du tuyau nommé auquel la sortie de débaille doit être envoyée.

*dwTimeout*<br/>
Le temps en millisecondes que cette classe attendra que le tuyau nommé devienne disponible.

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>CDebugReportHook::CDebugReportHook

Appels [CDebugReportHook::RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

La fonction de déclaration personnalisée qui est accrochée au processus de déclaration de débaillement C run-time.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Paramètres

*rapportType*<br/>
Le type de rapport (_CRT_WARN, _CRT_ERROR ou _CRT_ASSERT).

*message*<br/>
Chaîne du message.

*Returnvalue*<br/>
La valeur qui doit être retournée par [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Valeur de retour

Retourne FALSE si le crochet gère complètement le message en question afin qu’aucun autre rapport ne soit nécessaire. Retourne VRAI `_CrtDbgReport` si doit signaler le message de la manière normale.

### <a name="remarks"></a>Notes

La fonction de rapport tente d’ouvrir le tuyau nommé et de communiquer avec le processus à l’autre extrémité. Si le tuyau est occupé, la fonction de déclaration attendra jusqu’à ce que le tuyau soit libre ou que le délai d’expiration expire. Le délai d’attente peut être fixé par le constructeur ou un appel à [CDebugReportHook::SetTimeout](#settimeout).

Le code de cette fonction est exécuté dans le contexte de sécurité sous-jacent du thread d’appel, c’est-à-dire que l’usurpation d’identité est désactivée pour la durée de cette fonction.

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a>CDebugReportHook::RemoveHook

Appelez cette méthode pour arrêter d’envoyer des rapports de déboçon à la pipe nommée et restaurer le crochet de rapport précédent.

```cpp
void RemoveHook() throw();
```

### <a name="remarks"></a>Notes

Les [appels _CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) pour restaurer le crochet de rapport précédent.

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a>CDebugReportHook::SetHook

Appelez cette méthode pour commencer à envoyer des rapports de déboçon à la pipe nommée.

```cpp
void SetHook() throw();
```

### <a name="remarks"></a>Notes

Les [appels _CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) pour que les rapports de débaillement ont été acheminés par [CDebugReportHookProc](#cdebugreporthookproc) jusqu’au tuyau nommé. Cette classe garde une trace du crochet de rapport précédent afin qu’il puisse être restauré lorsque [RemoveHook](#removehook) est appelé.

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebugReportHook::SetPipeName

Appelez cette méthode pour régler la machine et le nom du tuyau auquel les rapports de débogé seront envoyés.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Paramètres

*szMachineName (en)*<br/>
Le nom de la machine à laquelle la sortie de débogé doit être envoyée.

*szPipeName (en)*<br/>
Le nom du tuyau nommé auquel la sortie de débaille doit être envoyée.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebugReportHook::SetTimeout

Appelez cette méthode pour régler le temps en millisecondes que cette classe attendra que le tuyau nommé devienne disponible.

```cpp
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
Le temps en millisecondes que cette classe attendra que le tuyau nommé devienne disponible.

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)
