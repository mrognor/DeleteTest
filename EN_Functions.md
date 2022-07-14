# Usefull library functions

## Split  
`std::vector<std::string> Split(std::string StringToSplit, std::string SplitterString=" ")`  
The function is needed for convenient work with incoming messages. 
Designed to split a string into a vector of strings. 
Divides by spaces by default, but you can set your own line for separation

## SendFile  
`bool SendFile(EN_SOCKET FileSendSocket, std::string FilePath, bool& IsStop, void (*ProgressFunction)(uint64_t current, uint64_t all, uint64_t speed, uint64_t eta) = nullptr, int DelayInMilliseconds = 0)`    
The function is needed to send files. The message receiving function should be called on the other side.  
* The first parameter is the socket for sending files  
* The second parameter is the full path to the file to be sent  
* The third parameter is a reference to a boolean variable to stop file transfer  
* The fourth parameter is a pointer to a function that is used to track the status of file transfer This function gets 4 parameters.  
	* The first is how many bytes were transmitted.  
	* The second is the total number of bytes.  
	* The third parameter shows the transfer rate in bytes.  
	* The fourth shows the remaining time in seconds  
* The fifth parameter is needed to regulate the file transfer rate. Gets milliseconds for the delay between sending chunks of the file  

By default, the library function is used to output to the console  
One kilobyte of data is transmitted at a time. If you make a delay of 100 milliseconds, 10 pieces or 10 kilobytes will be transmitted per second  

## RecvFile  
`bool RecvFile(EN_SOCKET& FileSendSocket, bool& IsStop, void (*ProgressFunction)(uint64_t current, uint64_t all, uint64_t speed, uint64_t eta) = nullptr)`    
The function is needed to receiving files.  
* The first parameter is the socket for receiving files  
* The second parameter is a reference to a boolean variable to stop file transfer 
* The fourth parameter is a pointer to a function that is used to track the status of file transfer This function gets 4 parameters.  
	* The first is how many bytes were transmitted.  
	* The second is the total number of bytes.  
	* The third parameter shows the transfer rate in bytes.  
	* The fourth shows the remaining time in seconds  


By default, the library function is used to output to the console

## DownloadStatus  
`void DownloadStatus(uint64_t current, uint64_t all, uint64_t speed, uint64_t eta)`
The function displays the status of the file transfer to the console
* The first is how many bytes were transmitted.  
* The second is the total number of bytes.  
* The third parameter shows the transfer rate in bytes.  
* The fourth shows the remaining time in seconds  

## IsFileExist  
`bool IsFileExist(std::string filePath)`  
Return true if file exists, otherwise rerurn false

## Delay
`void Delay(int milliseconds)`  
Crossplatform function for program suspension. Gets milliseconds