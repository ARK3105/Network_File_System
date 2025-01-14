
---

# Network File System (NFS) Project

This project implements a simplified version of a Network File System (NFS), which consists of three main components:

1. **Clients**: Systems or users requesting access to files within the network.
2. **Naming Server (NM)**: A central hub that manages file paths and coordinates between clients and storage servers.
3. **Storage Servers (SS)**: Responsible for storing and managing files and directories.

The NFS allows clients to perform file operations such as reading, writing, creating, deleting, and streaming audio files. The system also supports dynamic scalability, allowing storage servers to be added during runtime, and facilitates operations like file copying, listing, and getting metadata.

---

## Features Implemented

### 1. **Initialization**
   - Initialization of Naming Server (NM) and Storage Servers (SS).
   - The system ensures clients and servers can dynamically register and communicate with each other.

### 2. **Storage Server Functionalities**
   - **Add New Storage Servers**: New storage servers can be added dynamically after initialization.
   - **Client Interactions**:
     - Read and write files.
     - Get file size and permissions.
     - Stream audio files.
   - **Handling Commands**: The Naming Server can issue commands to Storage Servers for file creation, deletion, copying, and more.

### 3. **Client Functionalities**
   - **Path Finding**: Clients can request file operations (e.g., read, write, stream) via the Naming Server, which identifies the relevant storage server and provides the necessary details (IP, port).
   - **File Operations**: Clients can create, delete, and list files and folders.
   - **Copying Files/Directories**: Copying operations between different or same storage servers are supported.

### 4. **Asynchronous and Synchronous Writing**
   - Support for **asynchronous writing**, allowing large files to be written in chunks while providing an immediate acknowledgment to clients.
   - **Synchronous writing** can be prioritized by clients if the operation needs to be completed immediately.

### 5. **Multiple Client Support**
   - **Concurrent Client Access**: The system handles multiple clients simultaneously, with the Naming Server responding to multiple requests without blocking.
   - **Concurrency in File Operations**: Multiple clients can read the same file simultaneously, but write operations are exclusive.

### 6. **Error Handling**
   - Defined error codes for scenarios like file unavailability, write conflicts, and other failure conditions.

### 7. **Search and Caching in Naming Server**
   - **Efficient Search**: The Naming Server uses optimized data structures like Trie for fast path resolution.
   - **LRU Caching**: Recently accessed paths are cached for quicker response to subsequent requests.

### 8. **Backup and Data Replication**
   - **Failure Detection**: The system can detect when a storage server fails also the system can detect when a Storage Server reconnects.

### 9. **Logging and Message Display**
   - The Naming Server records logs for each request, acknowledgment, and error, including IP addresses and port information.

---

## Features To be Implemented

### 1. **Redundancy** (Bonus Feature)
   - The ensuring data is properly synchronized across the Storage Server's when they are back online.
   
### 2. **Backing Up Data**
   - ***Asynchronous Duplication***: Write operations are asynchronously replicated across storage servers for backup .
   - ***Replication***: Storing each file and folder in atleast two backup storage servers .

---

