---
title: _get_purecall_handler, _set_purecall_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
dev_langs:
- C++
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dca104d04546786a361c63461e502f7aa8b6127
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400273"
---
# <a name="getpurecallhandler-setpurecallhandler"></a>_get_purecall_handler, _set_purecall_handler

Obtient ou définit le gestionnaire d’erreurs pour un appel de fonction virtuelle pure.

## <a name="syntax"></a>Syntaxe

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Paramètres

*function*<br/>
Fonction à appeler quand une fonction virtuelle pure est appelée. A **_purecall_handler** fonction doit avoir un type de retour void.

## <a name="return-value"></a>Valeur de retour

Précédent **_purecall_handler**. Retourne **nullptr** s’il y a aucun gestionnaire précédent.

## <a name="remarks"></a>Notes

Le **_get_purecall_handler** et **_set_purecall_handler** fonctions sont spécifiques à Microsoft et s’appliquent uniquement au code C++.

Un appel à une fonction virtuelle pure est une erreur, car elle n’a pas d’implémentation. Par défaut, le compilateur génère du code pour appeler une fonction de gestionnaire d’erreurs quand une fonction virtuelle pure est appelée, ce qui met fin au programme. Vous pouvez installer votre propre fonction de gestionnaire d’erreurs pour les appels de fonctions virtuelles pures, de façon à les intercepter à des fins de débogage ou de création de rapports. Pour utiliser votre propre gestionnaire d’erreurs, créez une fonction qui possède le **_purecall_handler** signature, puis utilisez **_set_purecall_handler** afin de faciliter le gestionnaire en cours.

Étant donné qu’un seul **_purecall_handler** pour chaque processus, lorsque vous appelez **_set_purecall_handler** l’impact est immédiatement sur tous les threads. Le dernier appelant au niveau d'un thread est celui qui définit le gestionnaire.

Pour restaurer le comportement par défaut, appelez **_set_purecall_handler** en utilisant un **nullptr** argument.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_purecall_handler**, **_set_purecall_handler**|\<cstdlib> ou \<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// _set_purecall_handler.cpp
// compile with: /W1
#include <tchar.h>
#include <stdio.h>
#include <stdlib.h>

class CDerived;
class CBase
{
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function(void) = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase
{
public:
   CDerived() : CBase(this) {};   // C4355
   virtual void function(void) {};
};

CBase::~CBase()
{
   m_pDerived -> function();
}

void myPurecallHandler(void)
{
   printf("In _purecall_handler.");
   exit(0);
}

int _tmain(int argc, _TCHAR* argv[])
{
   _set_purecall_handler(myPurecallHandler);
   CDerived myDerived;
}
```

```Output
In _purecall_handler.
```

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
