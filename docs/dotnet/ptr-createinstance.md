---
title: PTR::CreateInstance | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.CreateInstance
- msclr::com::ptr::CreateInstance
- msclr.com.ptr.CreateInstance
- ptr::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- ptr::CreateInstance
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd4ba56b92150046b986f2b101f6a004c114bf28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161702"
---
# <a name="ptrcreateinstance"></a>ptr::CreateInstance
Crée une instance d’un objet COM dans un `com::ptr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   System::String ^ progid  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   const wchar_t * progid  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   REFCLSID rclsid  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `progid`  
 Chaîne `ProgID`.  
  
 `pouter`  
 Pointeur vers l’interface IUnknown de l’objet d’agrégation (IUnknown de contrôle). Si `pouter` n’est pas spécifié, `NULL` est utilisé.  
  
 `cls_context`  
 Contexte dans lequel s’exécutera le code qui gère l’objet nouvellement créé. Les valeurs sont extraites à partir de la `CLSCTX` énumération. Si `cls_context` n’est pas spécifié, la valeur CLSCTX_ALL est utilisée.  
  
 `rclsid`  
 `CLSID` associé avec les données et le code permettant de créer l’objet.  
  
## <a name="exceptions"></a>Exceptions  
 Si le `com::ptr` possède déjà une référence à un objet COM, `CreateInstance` lève <xref:System.InvalidOperationException>.  
  
 Cette fonction appelle `CoCreateInstance` et utilise <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pour toute erreur de conversion `HRESULT` à une exception appropriée.  
  
## <a name="remarks"></a>Notes  
 `CreateInstance` utilise `CoCreateInstance` pour créer une nouvelle instance de l’objet spécifié, identifié à partir d’un ProgID ou du CLSID. Le `com::ptr` fait référence à l’objet qui vient d’être créé et entraîne automatiquement la libération détenus toutes les références lors de sa destruction.  
  
## <a name="example"></a>Exemple  
 Cet exemple implémente une classe CLR qui utilise un `com::ptr` pour encapsuler son membre privé `IXMLDOMDocument` objet. Les constructeurs de classe utilisent deux formes de `CreateInstance` pour créer l’objet de document à partir d’un ProgID ou du CLSID plus un CLSCTX.  
  
```  
// comptr_createinstance.cpp  
// compile with: /clr /link msxml2.lib  
#include <msxml2.h>  
#include <msclr\com\ptr.h>  
  
#import <msxml3.dll> raw_interfaces_only  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
using namespace msclr;  
  
// a ref class that uses a com::ptr to contain an   
// IXMLDOMDocument object  
ref class XmlDocument {  
public:  
   // construct the internal com::ptr with a null interface  
   // and use CreateInstance to fill it  
   XmlDocument(String^ progid) {  
      m_ptrDoc.CreateInstance(progid);     
   }  
   XmlDocument(REFCLSID clsid, DWORD clsctx) {  
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      // create the class from a progid string  
      XmlDocument doc1("Msxml2.DOMDocument.3.0");  
  
      // or from a clsid with specific CLSCTX  
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Voir aussi  
 [ptr, membres](../dotnet/ptr-members.md)