import java.util.*;
import java.io.*;

public class MainForth {

	FastScanner in;
	PrintWriter out;
	
	
	public void solve() throws IOException {
		Forth x = new Forth();
		x.read();
		x.print(x.matrix);
		out.println("");
		x.print(x.transp());
		out.println("РАЗДЕЛИТЬ ВСЁ НА 3");
		x.print(x.fullSym());
		out.println("РАЗДЕЛИТЬ ВСЁ НА 3");
		x.print(x.fullAntiSym());
		out.println("РАЗДЕЛИТЬ ВСЁ НА 2");
		x.print(x.symIK());
		out.println("РАЗДЕЛИТЬ ВСЁ НА 2");
		x.print(x.antiSymJK());
		
	}

	public void run() {
		try {
			in = new FastScanner(new File("forth.in"));
			out = new PrintWriter(new File("forth.out"));

			solve();

			out.close();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	class Forth {
		public int[][][] matrix = new int[3][3][3];
		
		public void read() {
			for (int i = 0; i < 3; i++) {
				for (int k = 0; k < 3; k++) {
					for (int j = 0; j < 3; j++) {
						matrix[i][j][k] = in.nextInt();
					}
				}	
			}
		}
		
		public void print(int[][][] arr) {
			for (int i = 0; i < 3; i++) {
				for (int k = 0; k < 3; k++) {
					for (int j = 0; j < 3; j++) {
						 out.print(arr[i][j][k]);
						 out.print(" ");
					}
					out.print(" | ");
				}
				out.print("\n");
			}
		}
		
		private int sign(int i, int j, int k) {
			int num = 0;
			if (i > j) {
				num++;
			}
			if (i > k) {
				num++;
			}
			if (j > k) {
				num++;
			}
			if ((num % 2) == 0) {
			 return 1;
			}
			return -1;
		}
	
		private int signt(int i, int j) {
			if (i > j) {
				return -1;
			}
			return 1;
		}
		
		private int symElement(int i, int j, int k) {
			return (matrix[i][j][k] + matrix[i][k][j] + matrix[j][i][k] +
							matrix[j][k][i] + matrix[k][i][j] + matrix[k][j][i])/2;
		}
		
		private int antiSymElement(int i, int j, int k) {
			return (sign(i,j,k) * matrix[i][j][k] + sign(i,k,j) * matrix[i][k][j] 
							+ sign(j,i,k) * matrix[j][i][k] + sign(j,k,i) * matrix[j][k][i]
							+ sign(k,i,j) * matrix[k][i][j] + sign(k,j,i) * matrix[k][j][i])/2;
		}
		
		public int[][][] transp() {
			int[][][] trMatrix = new int[3][3][3];
			for (int i = 0; i < 3; i++) {
				for (int k = 0; k < 3; k++) {
					for (int j = 0; j < 3; j++) {
						trMatrix[i][j][k] = matrix[k][j][i];
					}
				}
			}
			return trMatrix;	
		}
		
		public int[][][] fullSym() {
			int[][][] sym = new int[3][3][3];
			for (int i = 0; i < 3; i++) {
				for (int k = 0; k < 3; k++) {
					for (int j = 0; j < 3; j++) {
						out.print(i + "," + j + "," + k + ": ");
						sym[i][j][k] = symElement(i, j, k);
						out.print(sym[i][j][k]);
						out.print(" ");
					}
					out.print(" | ");
				}
				out.print("\n");
			}
			out.println("");
			return sym;	
		}
		
		public int[][][] fullAntiSym() {
			int[][][] antiSym = new int[3][3][3];
			for (int i = 0; i < 3; i++) {
				for (int k = 0; k < 3; k++) {
					for (int j = 0; j < 3; j++) {
						out.print(i + "," + j + "," + k + ": ");
						antiSym[i][j][k] = antiSymElement(i, j, k);
						out.print(antiSym[i][j][k]);
						out.print(" ");
					}
					out.print(" | ");
				}
				out.print("\n");
			}
			out.println("");
			return antiSym;	
		}
		
		public int[][][] symIK() {
			int[][][] sym = new int[3][3][3];
			for (int i = 0; i < 3; i++) {
				for (int k = 0; k < 3; k++) {
					for (int j = 0; j < 3; j++) {
						sym[i][j][k] = (matrix[i][j][k] + matrix[k][j][i]);
					}
				}
			}
			return sym;
		}
		
		public int[][][] antiSymJK() {
			int[][][] antiSym = new int[3][3][3];
			for (int i = 0; i < 3; i++) {
				for (int k = 0; k < 3; k++) {
					for (int j = 0; j < 3; j++) {
						antiSym[i][j][k] = (matrix[i][j][k] - matrix[i][k][j]);
					}
				}
			}
			return antiSym;
		}
		
	}

	class FastScanner {
		BufferedReader br;
		StringTokenizer st;
		boolean Check;
		String line;

		FastScanner(File f) {
			try {
				br = new BufferedReader(new FileReader(f));
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			}
		}

		boolean getCheck() {
			return Check;
		}

		void setCheck(boolean b) {
			Check = b;
		}

		String next() {
			try {
				if (st == null || !st.hasMoreTokens()) {
					if ((line = br.readLine()) != null) {
						st = new StringTokenizer(line);
						setCheck(true);
					} else {
						setCheck(false);
					}
				}
			} catch (IOException e) {
				e.printStackTrace();
			}
			if (getCheck()) {
				return st.nextToken();
			} else {
				return "";
			} 
		}

		int nextInt() {
			return Integer.parseInt(next());
		}
	}

	public static void main(String[] args) {
		new MainForth().run();
	}
}
