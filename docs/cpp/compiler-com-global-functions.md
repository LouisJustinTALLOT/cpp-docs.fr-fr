---
title: Fonctions globales COM du compilateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb769cf1419f7a0142a5eeae348ca432f78fb92a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034135"
---
# <a name="compiler-com-global-functions"></a>Fonctions globales COM du compilateur

**Section spécifique à Microsoft**

Les routines suivantes sont disponibles :

|Fonction|Description|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Lève une [_com_error](../cpp/com-error-class.md) en réponse à une défaillance.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Remplace la fonction par défaut utilisée pour la gestion des erreurs COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convertit un `BSTR` valeur à un `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convertit un `char *` valeur à un `BSTR`.|

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)