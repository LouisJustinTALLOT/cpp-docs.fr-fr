---
title: Énumération de ATL_URL_SCHEME | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee13d34bcea1e7ce2e53b0659739ee730152f287
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755409"
---
# <a name="atlurlscheme"></a>ATL_URL_SCHEME  

Les membres de cette énumération fournissent des constantes pour les schémas compris par [CUrl](curl-class.md).

## <a name="syntax"></a>Syntaxe

```

      enum ATL_URL_SCHEME{  
   ATL_URL_SCHEME_UNKNOWN = -1,  
   ATL_URL_SCHEME_FTP     = 0,  
   ATL_URL_SCHEME_GOPHER  = 1,  
   ATL_URL_SCHEME_HTTP    = 2,  
   ATL_URL_SCHEME_HTTPS   = 3,  
   ATL_URL_SCHEME_FILE    = 4,  
   ATL_URL_SCHEME_NEWS    = 5,  
   ATL_URL_SCHEME_MAILTO  = 6,  
   ATL_URL_SCHEME_SOCKS   = 7  
};  
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

## <a name="see-also"></a>Voir aussi

[Concepts](../active-template-library-atl-concepts.md)   
[CUrl::SetScheme](curl-class.md#setscheme)   
[CUrl::GetScheme](curl-class.md#getscheme)