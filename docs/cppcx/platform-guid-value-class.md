---
title: Classe de valeur Platform::GUID | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c295138d6239ce516b4f322fb5fc479e2235a6be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089449"
---
# <a name="platformguid-value-class"></a>Classe de valeur Platform::Guid
Représente un type [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) dans le système de type Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public value struct Guid  
```  
  
### <a name="members"></a>Membres  
 Le Guid contient les méthodes Equals(), GetHashCode(), et ToString() dérivées de la [Platform::Object Class](../cppcx/platform-object-class.md), et la méthode GetTypeCode() dérivée de la [Platform::Type Class](../cppcx/platform-type-class.md). Le GUID comporte également les membres suivants.  
  
|Membre|Description|  
|------------|-----------------|  
|[Guid](#ctor)|Initialise une nouvelle instance du struct GUID.|  
|[operator==](#operator-equality)|Opérateur Equals.|  
|[!=, opérateur](#operator-not-equal)|Opérateur Not Equals.|  
|[operator()](#operator-call)|Convertit un Guid en GUID.|  
  
### <a name="remarks"></a>Notes  
 Pour un exemple de génération d'un nouveau Platform::Guid à l'aide de la fonction Windows [CoCreateGuid](http://msdn.microsoft.com/library/windows/desktop/ms688568\(v=vs.85\).aspx), consultez [Composant WinRT : comment générer un GUID ?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)  
  
### <a name="requirements"></a>Spécifications  
 **Minimum pris en charge le client :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd  

 
## <a name="ctor"></a> GUID::GUID, constructeurs
Initialise une nouvelle instance d'une structure de Guid.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  );  
  
    Guid(GUID m);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n );  
```  
  
### <a name="parameters"></a>Paramètres  
 `a`  
 Quatre premiers octets du GUID.  
  
 `b`  
 Deux octets suivants du GUID.  
  
 `c`  
 Deux octets suivants du GUID.  
  
 `d`  
 Octet suivant du GUID.  
  
 `e`  
 Octet suivant du GUID.  
  
 `f`  
 Octet suivant du GUID.  
  
 `g`  
 Octet suivant du GUID.  
  
 `h`  
 Octet suivant du GUID.  
  
 `i`  
 Octet suivant du GUID.  
  
 `j`  
 Octet suivant du GUID.  
  
 `k`  
 Octet suivant du GUID.  
  
 `m`  
 GUID défini.  
  
 `n`  
 Huit octets restants du GUID.  
  

## <a name="operator-equality"></a> GUID::operator ==, opérateur
Compare deux GUID.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::Guid::operator==  
```  
  
### <a name="return-value"></a>Valeur de retour  
 True si les deux GUID sont égaux.

## <a name="operator-inequality"></a> GUID::operator ! =, opérateur
Compare deux GUID.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::Guid::operator!=  
```  
  
### <a name="return-value"></a>Valeur de retour  
 True si les deux GUID ne sont pas égales.



## <a name="operator-call"></a> Opérateur de GUID::operator
Convertit implicitement un [structure GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)GUID Platform::GUID.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::Guid operator()  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Structure de GUID.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)