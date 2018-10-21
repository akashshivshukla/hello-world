import java.io.*;
import java.net.*;


public class ClientSideConnection {

	public static void main(String[] args) {
		
		try {
			
			Socket s = new Socket("localhost",5555);
			PrintWriter pw = new PrintWriter(s.getOutputStream());
			BufferedReader br_client_input = new BufferedReader(new InputStreamReader(System.in));
			BufferedReader br_server_output = new BufferedReader(new InputStreamReader(s.getInputStream()));
			
			String str_client = "";
			String str_server = "";
			while(!str_client.equals("stop")) {
				
				str_client = br_client_input.readLine();
				pw.println(str_client);
				pw.flush();
				if(!str_client.equals("stop")) { 
					str_server = br_server_output.readLine();
					System.out.println("Server : " + str_server);
					
				}	

			}
			br_client_input.close();
			br_server_output.close();
			s.close();
		}catch(IOException e) {
			
		}

	}

}
