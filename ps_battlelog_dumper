import requests


# function definitions 

def separate_files():
    # generates separate battle log text files per replay in input text file
    i = 0
    for i in range(0, len(line_array_new)-1):
        url = line_array_new[i] # extract url from array containing lines with .log at end
        req = requests.get(url) # request from server, store
        with open('{}.txt'.format(i), 'w', encoding='utf-8', errors='ignore') as final_file: # names files 0-n, n being last replay -1 cause python indeces
            final_file.write(req.text) # extract text from page
        i = i + 1
    return

def long_file():
    # generates one long text file of battle logs from all replays in input text file
    # separates each replay battle log entry with "Battle Log number "x" from "replay url" and 3 empty new lines
    i = 0    
    with open('battle_logs.txt', 'w', encoding='utf-8', errors='ignore') as final_file:   # names file battle_logs
        for i in range(0, len(line_array_new)-1):
            url = line_array_new[i]
            req = requests.get(url)
            final_file.write('Battle Log number {}'.format(i) + ' pulled from {}'.format(line_array_new[i]) + '\n\n\n')
            final_file.write(req.text)
            final_file.write('\n\n\n')
            i = i + 1
    return


# program 

print('\nBefore using, please make sure you only have replay URLs in the text file \n') # file pre processing reminder 
file_name = input('please specify text file name (without .txt) that contains replay urls: ') # take file name
line_array = [] # initialize array of lines in input file

with open(file_name + ".txt", 'r' ) as file_obj: # open file as condition to iterate over
    for line in file_obj: # iterate over lines
        line_array.append(line.strip()) # strip \n from each line, store in line array

line_array_new = [] # initialize new line array for new URLs

for i in range(0, len(line_array)-1):
   line_array_new.append(line_array[i] + ".log") # add ".log" to each replay url, store in new list


print('\nNow starting battle log download stage (This might take a while depending on how many replays you have!)\n')
print('\nDo you want to store battle logs as separate text files or as one large text file?\n')

types = {"1": separate_files, "2": long_file} # defines dictionary to call functions depending on input

selector = input('Enter 1 for separate text files or 2 for one large text file: ') # take input

types[selector]() # run function
