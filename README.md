***Windows APIs to Xojo data type conversion***

Here is a list of Windows types related to their Xojo equivalent, this is useful when you perform a Declare in Xojo.

Rule of thumb: ByRef and ByVal are only applicable to intrinsic data types (Integer, String, Double, Structures etc.) All arrays and object types are reference types, effectively behaving as if ByRef was used with an intrinsic data type.

If a parameter specifies OUT and is an intrinsic data type then it will need a ByRef so the value can be modified.

Remember: If you are calling a 32bit library from a 64bit application you may need to use use Int32 instead of Integer and UInt32 instead of UInteger.

Key: ? needs confirmation

```
Data type             Xojo type         Code
ACCESS_MASK           UInt32            name As UInt32
APIENTRY                                See WINAPI
ATOM                  UInt16            name As UInt16
BOOL                  Int32             name As Int32
                                           value=CType(name, Boolean)
                                           or
                                           name As Boolean (if binary values)
BOOLEAN               UInt8             name As UInt8
                                           value=CType(name, Boolean)
                                           or
                                           name As Boolean (if binary values)
BYTE                  Byte              name As Byte

CALLBACK                                See WINAPI
CCHAR                 Int8              name As Int8
CHAR                  Int8              name As Int8
CHAR *                See PCHAR 
                      or LPTSTR

COLORREF              UInt32 or Color ? See Color
CONST                 Const             name As (check call)
DOUBLE                Double            name As Double
DWORD                 UInt32            name As UInt32
DWORDLONG             UInt64            name As UInt64
DWORD_PTR             UInteger          name As UInteger
DWORD32               UInt32            name As UInt32
DWORD64               UInt64            name As UInt64
ENUM                  Int32             Used for enumeration that have no defined type
EXECUTION_STATE       UInt32            name As UInt32
FARPROC               Integer           name As Integer
FILEOP_FLAGS          UInt16            name As UInt16
FLOAT                 Single            name As Single
HACCEL                Integer           name As Integer
HALF_PTR              Int16 (x32)       Let me know if you find a use for this 
                      Int32 (x64)
                              
HANDLE                Integer           name As Integer
HBITMAP               Integer           name As Integer
HBRUSH                Integer           name As Integer
HCOLORSPACE           Integer           name As Integer
HCONV                 Integer           name As Integer
HCONVLIST             Integer           name As Integer
HCURSOR               Integer           name As Integer
HDC                   Integer           name As Integer
HDDEDATA              Integer           name As Integer
HDESK                 Integer           name As Integer
HDROP                 Integer           name As Integer
HDWP                  Integer           name As Integer
HENHMETAFILE          Integer           name As Integer
HFILE                 Int32             name As Int32
HFONT                 Integer           name As Integer
HGDIOBJ               Integer           name As Integer
HGLOBAL               Integer           name As Integer
HHOOK                 Integer           name As Integer
HICON                 Integer           name As Integer
HINSTANCE             Integer           name As Integer
HKEY                  Integer           name As Integer
HKL                   Integer           name As Integer
HLOCAL                Integer           name As Integer
HMENU                 Integer           name As Integer
HMETAFILE             Integer           name As Integer
HMODULE               Integer           name As Integer
HMONITOR              Integer           name As Integer
                      (W2000 onwards)
HPALETTE              Integer           name As Integer
HPEN                  Integer           name As Integer
HRESULT               Int32             name As Int32
HRGN                  Integer           name As Integer
HRSRC                 Integer           name As Integer
HSZ                   Integer           name As Integer
HWINSTA               Integer           name As Integer
HWND                  Integer or Ptr    name as Integer
                                        name As Ptr
INT                   Int32             name As Int32
INT_PTR               Integer           name As Integer
INT8                  Int8              name As Int8
INT16                 Int16             name As Int16
INT32                 Int32             name As Int32
INT64                 Int64             name As Int64
LANGID                UInt16            name As UInt16
LCID                  UInt32            name As UInt32
LCTYPE                UInt32            name As UInt32
LGRPID                UInt32            name As UInt32
LONG                  Int32             name As Int32
LONGLONG              Int64             name As Int64
LONG_PTR              Integer           name As Integer
LONG32                Int32             name As Int32
LONG64                Int64             name As Int64
LPARAM                Integer           name As Integer
LPBOOL                Int32             ByRef name As Int32
                                            value=CType(name, Boolean)
                                            or
                                            name As Ptr
                                            or
                                            name As Integer
LPBYTE                Byte              ByRef name As Byte
                                            or
                                            name As Ptr
                                            or
                                            name As Integer
LPCOLORREF            UInt32 or         ByRef name As UInt32
                      Color ?           name As Color See Color

LPCSTR                CString           name As CString
LPCTSTR               WString           name As WString
LPCVOID               UInt32 or         Const name As (check call) = xxx
                      See PVOID         ByRef name As (check call) (if intrinsic)
                                        name As (check call) (if NOT intrinsic)
LPCWSTR               WString           name As WString
LPDWORD               UInt32            ByRef name As UInt32
LPHANDLE              Integer           ByRef name As Integer
LPINT                 Int32             ByRef name As Int32
LPLONG                Int32             ByRef name As Long
LPSTR                 CString           name As CString
LPTSTR                WString           name As WString (unicode)
                      CString           name As CString (ansi) 
                      Ptr               If a value is returned, use:
                                           ByRef name As Ptr
                                           Dim tmp As New MemoryBlock(256)
                                           Dim p as Ptr = tmp
                                           // Make your call passing in p
                                           System.debuglog(tmp.CString(0))
                                           Note: allocate 2x more space for WString
LPVOID                See PVOID

LPWORD                UInt16            ByRef UInt16
LPWSTR                WString           See LPTSTR
LRESULT               Integer           name As Integer
NTSTATUS              Int32             name As Int32
NTSYSAPI              Int32             name As Int32
PBOOL                 Int32             ByRef name As Int32
                                          value=CType(name, Boolean)
PBOOLEAN              UInt8             ByRef name As UInt8
                                          value=CType(name, Boolean)
PBYTE                 Byte              ByRef name As Byte
PCHAR                 CString           name As CString
PCSTR                 CString           name As CString
PCTSTR                WString           name As WString (unicode)
                      CString           name As CString (ansi)
PCWSTR                WString           name As WString
PDWORD                UInt32            ByRef name As UInt32
PDWORDLONG            UInt64            ByRef name As UInt64
PDWORD_PTR            UInteger          ByRef name As UInteger
PDWORD32              UInt32            ByRef name As UInt32
PDWORD64              UInt64            ByRef name As UInt64
PFLOAT                Single            ByRef name As Single
PHALF_PTR             Int16 (x86)       ByRef name As Int16
                      Int32 (x64)       ByRef name As Int32
PHANDLE               Integer           ByRef name As Integer
PHKEY                 Integer           ByRef name As Integer
PINT                  Int32             ByRef name As Int32
PINT_PTR              Integer           ByRef name As Integer
PINT8                 Int8              ByRef name As Int8
PINT16                Int16             ByRef name As Int16
PINT32                Int32             ByRef name As Int32
PINT64                Int64             ByRef name As Int64
PLCID                 UInt32            ByRef name As UInt32
PLONG                 Int32             ByRef name As Int32
PLONGLONG             Int64             ByRef name As Int64
PLONG_PTR             Integer           ByRef name As Integer
PLONG32               Int32             ByRef name As Int32
PLONG64               Int64             ByRef name As Int64
POINTER_32            Integer           ByRef name As Integer
POINTER_64            Integer           ByRef name As Integer
POINTER_SIGNED        Integer           name As Integer
POINTER_UNSIGNED      UInteger          name As UInteger
PSHORT                Int16             ByRef name As Int16
PSIZE_T               UInteger          ByRef name As UInteger
PSSIZE_T              Integer           ByRef name As Integer
PSTR                  CString           name As CString
PTBYTE                UInt16            ByRef name As UInt16 (unicode)
                      Int8              ByRef name As Int8 (ansi)
PTCHAR                UInt16            ByRef name As UInt16 (unicode)
                      UInt8             ByRef name As UInt8 (ansi)
PTSTR                 WString           ByRef name As WString (unicode)
                      CString           ByRef name As CString (ansi)
PUCHAR                UInt8             ByRef name As UInt8
PUHALF_PTR            UInt16 (x86)      ByRef name As UInt16
                      UInt32 (x64)      ByRef name As UInt32
PUINT                 UInt32            ByRef name As UInt32
PUINT_PTR             UInteger          ByRef name As UInteger
PUINT8                UInt8             ByRef name As UInt8
PUINT16               UInt16            ByRef name As UInt16
PUINT32               UInt32            ByRef name As UInt32
PUINT64               UInt64            ByRef name As UInt64
PULONG                UInt32            ByRef name As UInt32
PULONGLONG            UInt64            ByRef name As UInt64
PULONG_PTR            UInteger          ByRef name As UInteger
PULONG32              UInt32            ByRef name As UInt32
PULONG64              UInt64            ByRef name As UInt64
PUSHORT               UInt16            ByRef name As UInt16
PVOID                 Ptr               name As Ptr (if using memoryblock)
                      (check call)      ByRef name As (check call) (if intrinsic)
                      (check call)      name As (check call) (if NOT intrinsic)
PWCHAR                WString           name As WString
PWORD                 UInt16            ByRef name As UInt16
PWSTR                 WString           ByRef name As WString
                      Ptr               name As Ptr (to memoryblock)
QWORD                 UInt64            name As UInt64
REGSAM                UInt32            name As UInt32
SC_HANDLE             Integer           name As Integer
SC_LOCK               See PVOID         
SERVICE_STATUS_HANDLE Integer           name As Integer
SHORT                 Int16             name As Int16
SIZE_T                UInteger          name As UInteger
SSIZE_T               Integer           name As Integer
TBYTE                 UInt16            ByRef name As UInt16 (unicode)
                      Int8              ByRef name As Int8 (ansi)
TCHAR                 UInt16            ByRef name As UInt16 (unicode)
                      UInt8             ByRef name As Int8 (ansi)
UCHAR                 UInt8             name As UInt8
UHALF_PTR             UInt16 (x86)      name As UInt16
                      UInt32 (x64)      name As UInt32
UINT                  UInt32            name As UInt32
UINT_PTR              UInteger          name As UInteger
UINT8                 UInt8             name As UInt8
UINT16                UInt16            name As UInt16
UINT32                UInt32            name As UInt32
UINT64                UInt64            name As UInt64
ULONG                 UInt32            name As UInt32
ULONGLONG             UInt64            name As UInt64
ULONG_PTR             UInteger          name As UInteger
ULONG32               UInt32            name As UInt32
ULONG64               UInt64            name As UInt64
UNICODE_STRING        Structure ?       Structure UNICODE_STRING
                                           Length As UInt16
                                           MaximumLength As UInt16
                                           Buffer As WString
                                        End Structure
USHORT                UInt16            name As UInt16
USN                   Int64             name As Int64
VARTYPE*              UInt16            name As UInt16
VOID                  Ptr               name As Ptr
                      (check call)      ByRef name As (check call)
                      (check call)      name As (check call)
                      (nothing)         (If there is no return, see Declare Sub)

WCHAR                 UInt16            name As UInt16
WCHAR name[128]       See code          name As String * 256 (in a structure)

WINAPI                                  Microsoft Win32 API calls are all StdCall so you might need:
                                           #Pragma X86CallingConvention StdCall

WNDPROC               Integer or Ptr    hWnd as Integer
                                        hWnd As Ptr
WORD                  UInt16            name As UInt16
WPARAM                UInteger          name As UInteger
                                        ByRef name As UInteger (if OUT)
                                        
STDMETHODCALLTYPE                       Note:
STDAPICALLTYPE                            #Pragma X86CallingConvention stdcall
STDMETHODCALLTYPE
STDAPICALLTYPE
STDAPI
STDAPI_(type)
STDMETHODIMP
STDMETHODIMP_(type)

STDMETHODVCALLTYPE                      Note:
STDAPIVCALLTYPE                           #Pragma X86CallingConvention cdecl
STDAPIVCALLTYPE
STDAPIV
STDAPIV_(type)
STDMETHODIMPV
STDMETHODIMPV_(type)
```


