---
description: 'En savoir plus sur : CDebugReportHook, classe'
title: CDebugReportHook (classe)
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
ms.openlocfilehash: 0b26965114caefb8727a34b99a7cacb30c415aac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141971"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook (classe)

Utilisez cette classe pour envoyer des rapports de débogage à un canal nommé.

## <a name="syntax"></a>Syntaxe

```
class CDebugReportHook
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDebugReportHook :: CDebugReportHook](#cdebugreporthook)|Appelle [SetPipeName](#setpipename), [setTimeout](#settimeout)et [SetHook](#sethook).|
|[CDebugReportHook :: ~ CDebugReportHook](#dtor)|Appelle [CDebugReportHook :: RemoveHook](#removehook).|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDebugReportHook :: CDebugReportHookProc](#cdebugreporthookproc)|Statique Fonction de création de rapports personnalisée qui est raccordée au processus de création de rapports de débogage du runtime C.|
|[CDebugReportHook :: RemoveHook](#removehook)|Appelez cette méthode pour arrêter d’envoyer des rapports de débogage au canal nommé et restaurer le hook de rapport précédent.|
|[CDebugReportHook :: SetHook](#sethook)|Appelez cette méthode pour commencer à envoyer des rapports de débogage au canal nommé.|
|[CDebugReportHook :: SetPipeName](#setpipename)|Appelez cette méthode pour définir l’ordinateur et le nom du canal auquel les rapports de débogage seront envoyés.|
|[CDebugReportHook :: SetTimeout](#settimeout)|Appelez cette méthode pour définir la durée en millisecondes pendant laquelle cette classe attend que le canal nommé soit disponible.|

## <a name="remarks"></a>Notes

Créez une instance de cette classe dans les versions Debug de vos services ou applications pour envoyer des rapports de débogage à un canal nommé. Les rapports de débogage sont générés en appelant [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) ou à l’aide d’un wrapper pour cette fonction, comme les macros [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) et [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) .

L’utilisation de cette classe vous permet de déboguer de manière interactive des composants s’exécutant dans des [stations de fenêtre](/windows/win32/winstation/window-stations)non interactives.

Notez que les rapports de débogage sont envoyés à l’aide du contexte de sécurité sous-jacent du thread. L’emprunt d’identité est temporairement désactivé afin que les rapports de débogage puissent être affichés dans les situations où l’emprunt d’identité des utilisateurs à faibles privilèges se produit, par exemple dans les applications Web.

## <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a> CDebugReportHook :: CDebugReportHook

Appelle [SetPipeName](#setpipename), [setTimeout](#settimeout)et [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Paramètres

*szMachineName*<br/>
Nom de l’ordinateur sur lequel la sortie de débogage doit être envoyée. La valeur par défaut est l’ordinateur local.

*szPipeName*<br/>
Nom du canal nommé auquel la sortie de débogage doit être envoyée.

*dwTimeout*<br/>
Durée en millisecondes pendant laquelle cette classe attend que le canal nommé soit disponible.

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a> CDebugReportHook :: ~ CDebugReportHook

Appelle [CDebugReportHook :: RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a> CDebugReportHook :: CDebugReportHookProc

Fonction de création de rapports personnalisée qui est raccordée au processus de création de rapports de débogage du runtime C.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Paramètres

*reportType*<br/>
Type du rapport (_CRT_WARN, _CRT_ERROR ou _CRT_ASSERT).

*message*<br/>
Chaîne du message.

*returnValue*<br/>
Valeur qui doit être retournée par [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur FALSe si le raccordement gère complètement le message en question afin qu’aucune autre génération de rapports ne soit requise. Retourne la valeur TRUE si `_CrtDbgReport` doit signaler le message de manière normale.

### <a name="remarks"></a>Notes

La fonction de création de rapports tente d’ouvrir le canal nommé et de communiquer avec le processus à l’autre extrémité. Si le canal est occupé, la fonction de création de rapports attend jusqu’à ce que le canal soit libre ou que le délai d’attente expire. Le délai d’attente peut être défini par le constructeur ou par un appel à [CDebugReportHook :: setTimeout](#settimeout).

Le code de cette fonction est exécuté dans le contexte de sécurité sous-jacent du thread appelant, autrement dit, l’emprunt d’identité est désactivé pendant toute la durée de cette fonction.

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a> CDebugReportHook :: RemoveHook

Appelez cette méthode pour arrêter d’envoyer des rapports de débogage au canal nommé et restaurer le hook de rapport précédent.

```cpp
void RemoveHook() throw();
```

### <a name="remarks"></a>Notes

Appelle [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) pour restaurer le hook de rapport précédent.

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a> CDebugReportHook :: SetHook

Appelez cette méthode pour commencer à envoyer des rapports de débogage au canal nommé.

```cpp
void SetHook() throw();
```

### <a name="remarks"></a>Notes

Appelle [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) pour que les rapports de débogage soient routés via [CDebugReportHookProc](#cdebugreporthookproc) vers le canal nommé. Cette classe effectue le suivi du hook de rapport précédent afin qu’il puisse être restauré quand [RemoveHook](#removehook) est appelé.

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a> CDebugReportHook :: SetPipeName

Appelez cette méthode pour définir l’ordinateur et le nom du canal auquel les rapports de débogage seront envoyés.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Paramètres

*szMachineName*<br/>
Nom de l’ordinateur sur lequel la sortie de débogage doit être envoyée.

*szPipeName*<br/>
Nom du canal nommé auquel la sortie de débogage doit être envoyée.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a> CDebugReportHook :: SetTimeout

Appelez cette méthode pour définir la durée en millisecondes pendant laquelle cette classe attend que le canal nommé soit disponible.

```cpp
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
Durée en millisecondes pendant laquelle cette classe attend que le canal nommé soit disponible.

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)
